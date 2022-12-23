# add
task 5 kyu 
https://www.codewars.com/kata/55f4e56315a375c1ed000159
my sol 
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
	
  fav sol 
  public class PowerSumDig {
    
    public static long powerSumDigTerm(int n) {

        long[] arr = {81, 512, 2401, 4913, 5832, 17576, 19683, 234256, 390625, 614656, 1679616, 17210368, 34012224, 52521875, 60466176,
            205962976, 612220032, 8303765625L, 10460353203L, 24794911296L, 27512614111L, 52523350144L, 68719476736L, 271818611107L, 1174711139837L,
            2207984167552L, 6722988818432L, 20047612231936L, 72301961339136L, 248155780267521L, 3904305912313344L, 45848500718449031L, 81920000000000000L, 150094635296999121L};
        return arr[n-1];
    }
}

task 5 kyu 
https://www.codewars.com/kata/51edd51599a189fe7f000015/solutions/java?filter=all&sort=oldest&invalids=false
my sol 
public class Solution {
  public static double solution(int[] arr1, int[] arr2) {
    int sum = 0;
    for (int i = 0; i < arr1.length; i++) {
      sum += Math.pow(Math.abs(arr1[i] - arr2[i]), 2);
    }
    return (double)sum / arr1.length;
  }
}
fav 
public class Solution {
    public static double solution(int[] arr1, int[] arr2) {
        return java.util.stream.IntStream.range(0, arr1.length).map(i -> arr1[i] - arr2[i]).map(diff -> diff * diff).average().getAsDouble();
    }
}

task 5 kyu
https://www.codewars.com/kata/54f8693ea58bce689100065f
my sol
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
fav 
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
task 5 kyu 
https://www.codewars.com/kata/635b8fa500fba2bef9189473/java
my sol
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
fav 
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

task 4 kyu 
https://www.codewars.com/kata/51ba717bb08c1cd60f00002f/java
my sol 
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
fav sol 
class Solution {
		public static String rangeExtraction(int[] arr) {
        String str = String.valueOf(arr[0]);
        for (int i = 1; i < arr.length; i++)
            str += (arr[i-1] == arr[i]-1 ? "<":",") + String.valueOf(arr[i]);
        return str.replaceAll("<([^,]*<)+","-").replaceAll("<",",");
    }
}

task 5 kyu 
https://www.codewars.com/kata/61fef3a2d8fa98021d38c4e5/java
my sol
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
fav 
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
