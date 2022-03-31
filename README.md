# caesar-cipher-java
cipher
public class Solution {
    static final String text = "I love Javaz.";
    static final int key = -15;
    static final char[] alphabet = {'\n', ' ', '.', '!', 'a', 'b', 'c', 'd',
            'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l',
            'm', 'n', 'o', 'p', 'q', 'r', 's', 't',
            'u', 'v', 'w', 'x', 'y', 'z'};
    public static void main(String[] args) {
        String encrypted = encrypt(text, key, alphabet);
        System.out.println(encrypted);
        String decrypted = decrypt(encrypted, key, alphabet);
        System.out.println(decrypted);
    }

    // метод для шифрования строки
    private static String encrypt(String text, int key, char[] alphabet) {
        String result = "";
        String textToLowerCase = text.toLowerCase();
        char[] array = textToLowerCase.toCharArray();
        int index = 0;
        for (int i = 0; i < text.length(); i++) {

            char letter = array[i];
            for (int j = 0; j < alphabet.length; j++) {
                if(letter == alphabet[j]){
                    index = j;
                }
            }
            int newIndex = (alphabet.length + index + key)%alphabet.length;
            char encryptedLetter = alphabet[newIndex];
            result += encryptedLetter;
        }
        return result;
    }

    // метод для дешифровки строки
    private static String decrypt(String text, int key, char[] alphabet) {
        String result = "";
        String textToLowerCase = text.toLowerCase();
        char[] array = textToLowerCase.toCharArray();
        int index = 0;
        for (int i = 0; i < text.length(); i++) {

            char letter = array[i];
            for (int j = 0; j < alphabet.length; j++) {
                if(letter == alphabet[j]){
                    index = j;
                }
            }
            int newIndex = (alphabet.length + index - key)%alphabet.length;
            char decryptedLetter = alphabet[newIndex];
            result += decryptedLetter;
        }
        return result;
    }

}
