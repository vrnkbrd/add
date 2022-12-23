# add
#This is additional file where I diwnloaded all the tasks that I solved for some extra points
### Task 5 kyu 
https://www.codewars.com/kata/513e08acc600c94f01000001
The rgb function is incomplete. Complete it so that passing in RGB decimal values will result in a hexadecimal representation being returned. Valid decimal values for RGB are 0 - 255. Any values that fall out of that range must be rounded to the closest valid value.

### My solution 
```Java
public class RgbToHex {

    public static String rgb(int r, int g, int b) {
        return ( toHexString ( r ) + toHexString ( g ) + toHexString ( b ) ).toUpperCase ();
    }

    private static String toHexString ( int k )
    {
        if ( k <= 0 )
        {
            return "00";
        }

        if ( k >= 255 )
        {
            return "FF";
        }

        String hex = Integer.toHexString ( k ).toUpperCase ();
        if ( hex.length () == 1 )
        {
            hex = "0" + hex;
        }

        return hex;
    }
}
```

### Fav solution
```Java
public class RgbToHex {

    public static String rgb(int r, int g, int b) {
        if(r < 0) r = 0;
        if(g < 0) g = 0;
        if(b < 0) b = 0;
        if(r > 255) r = 255;
        if(g > 255) g = 255;
        if(b > 255) b = 255;

        return String.format("%02X%02X%02X", r, g, b);
    }
}
```
Iconic 

### Task 5 kyu 
https://www.codewars.com/kata/55f4e56315a375c1ed000159
### My solution
```Java
import java.util.ArrayList;
import java.util.Collections;

public class PowerSumDig {
    
    public static long powerSumDigTerm(int n) {
		
		ArrayList<Long> listresults= new ArrayList<>(); 
		
		for(int i = 2 ; i < 100; i++){
			for(int j = 2; j < 200; j++){
				long result =  (long) Math.pow(i, j);
				if(i == digitSum(result)){
					listresults.add(result);
				}
			}
		}
		Collections.sort(listresults);
		return listresults.get(n-1);
		
	 }   

	
	public static int digitSum(long v) {
        int sum = 0;
        while (v > 0) {
            sum += v % 10;
            v /= 10;
        }
        return sum;
    }
```	
###Fav solution
```Java
  public class PowerSumDig {
    
    public static long powerSumDigTerm(int n) {

        long[] arr = {81, 512, 2401, 4913, 5832, 17576, 19683, 234256, 390625, 614656, 1679616, 17210368, 34012224, 52521875, 60466176,
            205962976, 612220032, 8303765625L, 10460353203L, 24794911296L, 27512614111L, 52523350144L, 68719476736L, 271818611107L, 1174711139837L,
            2207984167552L, 6722988818432L, 20047612231936L, 72301961339136L, 248155780267521L, 3904305912313344L, 45848500718449031L, 81920000000000000L, 150094635296999121L};
        return arr[n-1];
    }
}
```
###Task 5 kyu 
https://www.codewars.com/kata/51edd51599a189fe7f000015/solutions/java?filter=all&sort=oldest&invalids=false
### My solution
```Java
public class Solution {
  public static double solution(int[] arr1, int[] arr2) {
    int sum = 0;
    for (int i = 0; i < arr1.length; i++) {
      sum += Math.pow(Math.abs(arr1[i] - arr2[i]), 2);
    }
    return (double)sum / arr1.length;
  }
}
```
### Fav solution
```Java
public class Solution {
    public static double solution(int[] arr1, int[] arr2) {
        return java.util.stream.IntStream.range(0, arr1.length).map(i -> arr1[i] - arr2[i]).map(diff -> diff * diff).average().getAsDouble();
    }
}
Streams and maps structures were used. The solution is incrediblel short
```
### Task 5 kyu
https://www.codewars.com/kata/54f8693ea58bce689100065f
### My solution
```Java
class Decomp {
  public static String decomposeAux(String nrStr, String drStr) {
    long nr = Long.parseLong(nrStr);
    long dr = Long.parseLong(drStr);
    if (dr == 0 || nr == 0) {
          return "";
    }
      if (dr % nr == 0)
        return "1/" + dr / nr;
      String res = "";
    if (nr > dr) {
      long q = (int)Math.floor((double)(nr / dr));
      res += q + "";
      if (nr % dr != 0) {
        res += ", " + decomposeAux(Long.toString(nr % dr), Long.toString(dr));
        return res.trim();
      }
      else return res.trim();
    }
    long n = dr / nr + 1;
    res += "1/" + n + ", ";
      res += decomposeAux(Long.toString(nr * n - dr), Long.toString(dr * n));
    return res.trim();
  }
  public static String decompose(String nrStr, String drStr) {
      String res = decomposeAux(nrStr, drStr);
      return "[" + res + "]";
  }
}
```
### Fav solution
```Java
class Decomp {
  
  public static String decompose(String nrStr, String drStr) {
      long a = Integer.parseInt(nrStr);
      long b = Integer.parseInt(drStr);
      long denum = 2;
      String s;
      if (a>b){
        s = ", "+a/b;
        a %= b;
      } else s = "";
      while(a>0){
          if (a*denum>=b){
              s += ", 1/"+denum;
              a = a*denum-b;
              b *= denum;
          }
          denum++;
      }        
      return s.isEmpty()?"[]":"["+s.substring(2)+"]";
}
}
```

### Task 5 kyu 
https://www.codewars.com/kata/635b8fa500fba2bef9189473/java
### My solution
```Java
public class PhoneWords {
  public static String phoneWords(String str) {
    StringBuilder sb = new StringBuilder();
		char[][] letters = {{' '}, //0
	    					{'1'}, //1
	    					{'a', 'b', 'c'}, //2
	    					{'d', 'e', 'f'}, //3
	    					{'g', 'h', 'i'}, //4
	    					{'j', 'k', 'l'}, //5
	    					{'m', 'n', 'o'}, //6
	    					{'p', 'q', 'r', 's'}, //7
	    					{'t', 'u', 'v'}, //8
	    					{'w', 'x', 'y', 'z'} //9
	    				  };
	    if(str == null || str.isEmpty()) return "";
	    int num_curr = 0, num_next = 0, contCurr = 0;
	    
    	num_next = Integer.parseInt(str.substring(0, 1));
	    
	    for(int i = 0; i < str.length()-1; i++) {
	    	num_curr = Integer.parseInt(str.substring(i, i+1));
	    	num_next = Integer.parseInt(str.substring(i+1, i+2));
	    	
	    	if(num_curr == 1) contCurr = 0;
	    	
	    	if(num_curr == num_next && contCurr < letters[num_curr].length-1)
	    		contCurr++;
	    	else {
	    		if(num_curr != 1) {	    			
	    			contCurr++;
	    			sb.append(letters[num_curr][contCurr > 0 ? contCurr-1 : 0]);
	    		}
	    		contCurr = 0;
	    	}
	    }
	    
	    char lastChar = letters[num_next][contCurr > 0 ? ++contCurr-1 : 0];
	    sb.append(lastChar != '1' ? lastChar : "");
		return sb.toString();
  }  
}
```
### Fav solution
```Java
public class PhoneWords {
  
  public static String phoneWords(String str) {
    // 416666663105558822255
    System.out.println(str);
    return str == null || str.isBlank() ? "" : str
                        .replaceAll("222", "c")
                        .replaceAll("22", "b")
                        .replaceAll("2", "a")
                        .replaceAll("333", "f")
                        .replaceAll("33", "e")
                        .replaceAll("3", "d")
                        .replaceAll("444", "i")
                        .replaceAll("44", "h")
                        .replaceAll("4", "g")
                        .replaceAll("555", "l")
                        .replaceAll("55", "k")
                        .replaceAll("5", "j")
                        .replaceAll("666", "o")
                        .replaceAll("66", "n")
                        .replaceAll("6", "m")
                        .replaceAll("7777", "s")
                        .replaceAll("777", "r")
                        .replaceAll("77", "q")
                        .replaceAll("7", "p")
                        .replaceAll("888", "v")
                        .replaceAll("88", "u")
                        .replaceAll("8", "t")
                        .replaceAll("9999", "z")
                        .replaceAll("999", "y")
                        .replaceAll("99", "x")
                        .replaceAll("9", "w")
                        .replaceAll("0", " ")
                        .replaceAll("1", "");
  }  
  
}
```

### Task 4 kyu 
https://www.codewars.com/kata/51ba717bb08c1cd60f00002f/java
### My solution
```Java
class Solution {
		public static String rangeExtraction(int[] arr) {
    		String ans = "";
		
		for(int e = 0; e<arr.length; e++){
			for(int j = arr.length-1; j>=e; j--){
				if(arr[j]-arr[e]==j-e && j-e >= 2){
					ans+=arr[e]+"-"+arr[j]+",";
					e=j;
					j=0;
				}else if(j==e){
					ans+=arr[e]+",";
				}
			}
			
		}
		
		return ans.substring(0, ans.length()-1);
    }
}
```
### Fav solution
```Java
class Solution {
		public static String rangeExtraction(int[] arr) {
        String str = String.valueOf(arr[0]);
        for (int i = 1; i < arr.length; i++)
            str += (arr[i-1] == arr[i]-1 ? "<":",") + String.valueOf(arr[i]);
        return str.replaceAll("<([^,]*<)+","-").replaceAll("<",",");
    }
}
```
### Task 5 kyu  
https://www.codewars.com/kata/61fef3a2d8fa98021d38c4e5/java
### My solution
```Java
class Solution {
  public static long cardGame(long n) {
    return f(n, 0, new long[] {0, 0})[0];
  }
  
  static long[] f(long n, int turn, long[] state) {
    if (n == 0) return state;
    if (n % 2 == 1) {
      n--;
      state[turn]++;
    } else if (n < 10 || n % 4 > 0) {
      n /= 2;
      state[turn] += n;
    } else {
      n--;
      state[turn]++;
    }
    return f(n, 1 - turn, state);
  }
}
```
### Fav solution
```Java
class Solution {
  public static long cardGame(long N) {
    long s=0;
    while(N>0){
      s+= pick(N);
      N = remain(remain(N));
    }
    return s;
  }
  
  static private long pick(long N)     { return getOne(N) ? 1L : N/2L; }
  static private long remain(long N)   { return getOne(N) ? N-1L : N/2L; }
  
  static private boolean getOne(long N){ return N%2L==1 || N>4L && N/2L%2==0; }
}
``` 

### Task 5 kyu 
https://www.codewars.com/kata/529adbf7533b761c560004e5/solutions/javascript
### My solution
```Java
var fibonacci = function () {
  var m = function(n,formula) { 
    return (m[n] || (m[n]=formula())); 
  };
  return function(n) {
    if(n===0 || n===1) 
      return n 
    return m(n, function() { return fibonacci(n-1) + fibonacci(n-2); });
  };
}();
```
### Fav solution
```Java
var fibonacci = (function () {
  var cache = {};
  
  return function(n) {
    
    // Base case
    if(n==0 || n == 1)
        return n;
    
    // Recurse only if necessary
    if(cache[n-2] === undefined)
      cache[n-2] = fibonacci(n-2);
    if(cache[n-1] === undefined)
      cache[n-1] = fibonacci(n-1);
    
    return cache[n-1] + cache[n-2];
  };
})(); // Immediately invoke to create a closure for the cache variable
```

### Task 4 kyu 
https://www.codewars.com/kata/52a382ee44408cea2500074c/java
### My solution
```Java
import java.util.BitSet;

public class Matrix {

    private final int[][] matrix;
    private final BitSet removedColumns;

    private Matrix(int[][] matrix) {
        this.matrix = matrix;
        this.removedColumns = new BitSet(matrix.length);
    }

    private int determinant(int step) {
        if (step==matrix.length) {
            return 1;
        }
        int result = 0;
        int multiplier = 1;
        int[] firstRow = matrix[step];
        for (int j = 0; j < firstRow.length; j++) {
            if (removedColumns.get(j)) {
                continue;
            }
            removedColumns.set(j);
            result += multiplier * firstRow[j] * determinant(step+1);
            removedColumns.clear(j);
            multiplier *= -1;
        }
        return result;
    }

    public static int determinant(int[][] matrix) {
        return new Matrix(matrix).determinant(0);
    }
}
```
### Fav solution 
```Java
public class Matrix {
    
    public static int determinant(int[][] m) {
        int d = 0, size = m.length;
        if (size == 1) return m[0][0];
        
        for (int n = 0 ; n < size ; n++) {
            int[][] newM = new int[size-1][size-1];
            for (int x = 1 ; x < size ; x++) for (int y = 0 ; y < size ; y++) {
                if (y == n) continue;
                newM[x-1][y + (y>n ? -1 : 0)] = m[x][y];
            }
            d += (n%2!=0 ? -1 : 1) * m[0][n] * determinant(newM);
        }
        return d;
    }
}
```
### task 5 kyu 
https://www.codewars.com/kata/5541f58a944b85ce6d00006a/java
### My solution
```Java
public class ProdFib { // must be public for codewars	
	
	public static long[] productFib(long prod) {
  
      long prodTotal = 0;
      long fibFirst = 0;
      long fibSecond = 1;
      
      while(prodTotal < prod){        
        long fibNumber = fibFirst + fibSecond;
        fibFirst = fibSecond;
        fibSecond = fibNumber;
        prodTotal = fibFirst * fibSecond;
      }
      
      if(prodTotal == prod){
          return new long[]{fibFirst, fibSecond, 1};
      } else {
          return new long[]{fibFirst, fibSecond, 0};
      }
   }
}
```
### Fav solution
```Java
public class ProdFib { // must be public for codewars	
	
	public static long[] productFib(long prod) {
		long a = 0L;
    long b = 1L;
    while (a * b < prod) {
      long tmp = a;
      a = b;
      b = tmp + b;
    }
    return new long[] { a, b, a * b == prod ? 1 : 0 };
   }
}
```
### Task 5 kyu 
https://www.codewars.com/kata/526dbd6c8c0eb53254000110/java
### My solution
```Java
public class SecureTester{
  
  public static boolean alphanumeric(String s){
    if(s.length()==0) return false;
    for(int j =0; j < s.length(); j++) {
      char c = s.charAt(j);
      if((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') || (c >= '0' && c <= '9')) continue;
      else return false; 
  }
return true;
}
  }
  ```
### Fav solution
```Java 
public class SecureTester {
  public static boolean alphanumeric(String s) {
    return s.matches("[A-Za-z0-9]+");
  }
}
Very short and exclusive sol
```

### Task 5 kyu 
https://www.codewars.com/kata/55a29405bc7d2efaff00007c/java
### My solution
```Java
public class Suite {
	
	public static double going(int n) {
		  double r = 1.0; double k = 1.0;
    	for (int i = n; i >=2; i--) {
        	k = k * (1.0 / i);
        	r += k;
		  }
    	return Math.floor(r * Math.pow(10, 6)) / Math.pow(10, 6);
	}
}
```
### Fav solution
```Java
public class Suite {
	
	public static double going(int n) {
		  double result = 1.0;
      double frac = 1.0;
      while (n > 1) {
          frac /= n--;
          result += frac;
      }
      return (int) (result * 1e6) / 1e6;
	}
}
```
