## Java Programs
 ### 1. java polindrome string ?
```java
public class PalindromeChecker {
    public static boolean isPalindrome(String str) {
        int left = 0, right = str.length() - 1;
        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }

    public static void main(String[] args) {
        String str = "madam";
        System.out.println(isPalindrome(str)); // Output: true
    }
```
 ### 2. java polindrome number ?
 ```java
public class PalindromeNumberChecker {
    private static boolean isPalindromeNumber(long number) {
    		if (number < 0 || (number % 10 == 0 && number != 0))
			    return false; // Negative numbers and numbers ending in 0 (except 0) are not palindromes

		    long reversedHalf = 0;
	    	while (number > reversedHalf) {
			    reversedHalf = reversedHalf * 10 + number % 10; // Reverse only half
	     	number /= 10; // Reduce original number
	    	}

	  // A palindrome must match the original first half and reversed second half
		  return (number == reversedHalf || number == reversedHalf / 10);
	}


    public static void main(String[] args) {
        long str = "575";
        System.out.println(isPalindromeNumber(str)); // Output: true
    }
```

