# RomanToInteger
package com.pattern;
	import java.util.ArrayList;
	import java.util.Collections;
	import java.util.List;
	import java.util.Scanner;
	public class even {
	    public static void main(String[] args) {
	        List<Integer> numberList = new ArrayList<>();
	        numberList.add(1);
	        numberList.add(2);
	        numberList.add(3);
	        numberList.add(4);
	        numberList.add(5);
	        numberList.add(6);
	        numberList.add(7);
	        Collections.shuffle(numberList);
	        System.out.println("Shuffled array: " + numberList);
	        Scanner sc = new Scanner(System.in);
	        System.out.print("Enter a Roman numeral: ");
	        String romanNumeral = sc.nextLine().toUpperCase();
	        int romanToInteger = romanToInteger(romanNumeral);
	        System.out.println("Roman numeral converted to integer: " + romanToInteger);
	        System.out.print("Enter a sentence: ");
	        String inputSentence = sc.nextLine();
	        if (isPangram(inputSentence)) {
	            System.out.println("The input is a pangram.");
	        } else {
	            System.out.println("The input is not a pangram.");
	        }
	    }
	    public static int romanToInteger(String s) {
	        int result = 0;
	        int prevValue = 0;

	        for (int i = s.length() - 1; i >= 0; i--) {
	            int currentValue = romanValue(s.charAt(i));
	            if (currentValue < prevValue) {
	                result -= currentValue;
	            } else {
	                result += currentValue;
	            }
	            prevValue = currentValue;
	        }
	        return result;
	    }
	    public static int romanValue(char c) {
	        switch (c) {
	            case 'I':
	                return 1;
	            case 'V':
	                return 5;
	            case 'X':
	                return 10;
	            case 'L':
	                return 50;
	            case 'C':
	                return 100;
	            case 'D':
	                return 500;
	            case 'M':
	                return 1000;
	            default:
	                return 0;
	        }
	    }
	    public static boolean isPangram(String sentence) {
	        boolean[] alphabet = new boolean[26];
	        sentence = sentence.toLowerCase();

	        for (int i = 0; i < sentence.length(); i++) {
	            char c = sentence.charAt(i);
	            if (c >= 'a' && c <= 'z') {
	                alphabet[c - 'a'] = true;
	            }
	        }
	        for (boolean letter : alphabet) {
	            if (!letter) {
	                return false;
	            }
	        }

	        return true;
	    }
	}
