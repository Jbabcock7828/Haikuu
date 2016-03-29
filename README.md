# Haikuu
import java.io.File;
import java.io.FileNotFoundException;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;


public class Haiku {
	public static String theFile = "C:\\Users\\JeremiahBabcock\\Desktop\\guten_text.txt";
	public int countSyllables(String word) {
	    int count = 0;
	    word = word.toLowerCase();
	    for (int i = 0; i < word.length(); i++) {
	        if (word.charAt(i) == '\"' || word.charAt(i) == '\'' || word.charAt(i) == '-' || word.charAt(i) == ',' || word.charAt(i) == ')' || word.charAt(i) == '(') {
	            word = word.substring(0,i)+word.substring(i+1, word.length());
	        }
	    }
	    boolean isPrevVowel = false;
	    for (int j = 0; j < word.length(); j++) {
	        if (word.contains("a") || word.contains("e") || word.contains("i") || word.contains("o") || word.contains("u")) {
	            if (isVowel(word.charAt(j)) && !((word.charAt(j) == 'e') && (j == word.length()-1))) {
	                if (isPrevVowel == false) {
	                    count++;
	                    isPrevVowel = true;
	                }
	            } else {
	                isPrevVowel = false;
	            }
	        } else {
	            count++;
	            break;
	        }
	    }
	    System.out.println(count + "Syllables");
	    return count;
	}

	private boolean isVowel(char c) {
	        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ) {
	            return true;
	        } else {
	            return false;
	        }
	    } ////Users/JeremiahBabcock/Documents/Computer Prog. 2/workspace/Java Refresher/src
public void fileReader(){
	 try {
		String word = "";
		@SuppressWarnings("resource")
		Scanner inFile1 = new Scanner(new File(theFile)).useDelimiter("[\\s ]+");
		List<String> temps = new ArrayList<String>();
	    while (inFile1.hasNext()) {
	      word = inFile1.next().trim();
	     if(word != null){
	    	 word = word.toLowerCase();
	    	 temps.add(word);
	     }
	      }
	    inFile1.close();
	 } catch (FileNotFoundException e) {
		System.out.println("Trouble while reading file!");
		e.printStackTrace();
	}
	 }
public static void main(String[] args){
	Haiku hi = new Haiku();
    hi.countSyllables("interesting");
}
}
