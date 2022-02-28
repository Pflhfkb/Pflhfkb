package zadanie;

import java.util.Scanner;

public class Main {
    static Scanner scanner = new Scanner(System.in);
    static int nom1, nom2;
    static char operation;
    static int result;

    public static void main (String[] args) {
        exit:
        {
            System.out.println("Введите выражение (арабскими или римскими цифрами) + (Enter)");
            String userInput = scanner.nextLine();
            char[] massIn = new char[9];
            for (int i = 0; i < userInput.length(); i++) {
                massIn[i] = userInput.charAt(i);
                if (massIn[i] == '+') {
                    operation = '+';
                }
                if (massIn[i] == '-') {
                    operation = '-';
                }
                if (massIn[i] == '*') {
                    operation = '*';
                }
                if (massIn[i] == '/') {
                    operation = '/';
                }
            }
            String sumbolIn = String.valueOf(massIn);
            String[] sumbolSplit = sumbolIn.split("[+-/*]");
            if (sumbolSplit.length > 2){
                System.out.println("Некорректный ввод");
                break exit;
                //kos();
            }

            String sumbol1 = sumbolSplit[0];
            String sumbol2 = sumbolSplit[1].trim();
            nom1 = romanToNumber(sumbol1);
            nom2 = romanToNumber(sumbol2);
            if ((nom1 < 0 && nom2 > 0) || (nom1 > 0 && nom2 < 0)) {
                //kos();
                System.out.println("Некорректный ввод");
                break exit;
            }
            if (nom1 < 0 && nom2 < 0) {
                result = 0;
            } else {
                result = calc(nom1, nom2, operation);
                String resultRoman = converter(result);
                System.out.printf("%s" + operation + "%s=%s\n", sumbol1, sumbol2, resultRoman);
                break exit;
                //System.ексит(0);
            }
            nom1 = Integer.parseInt(sumbol1);
            nom2 = Integer.parseInt(sumbol2);
            if (nom1 > 10 || nom2 > 10) {
                System.out.println("Некорректный ввод");
                break exit;
                //kos();
            }
            result = calc(nom1, nom2, operation);
            System.out.printf("%s" + operation + "%s=%s\n", nom1, nom2, result);
        }
    }

    private static String converter (int numArabian) {
        String[] roman = {"O", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X", "XI", "XII", "XIII", "XIV", "XV", "XVI", "XVII", "XVIII", "XIX", "XX",
                "XXI", "XXII", "XXIII", "XXIV", "XXV", "XXVI", "XXVII", "XXVIII", "XXIX", "XXX", "XXXI", "XXXII", "XXXIII", "XXXIV", "XXXV", "XXXVI", "XXXVII", "XXXVIII", "XXXIX", "XL",
                "XLI", "XLII", "XLIII", "XLIV", "XLV", "XLVI", "XLVII", "XLVIII", "XLIX", "L", "LI", "LII", "LIII", "LIV", "LV", "LVI", "LVII", "LVIII", "LIX", "LX",
                "LXI", "LXII", "LXIII", "LXIV", "LXV", "LXVI", "LXVII", "LXVIII", "LXIX", "LXX",
                "LXXI", "LXXII", "LXXIII", "LXXIV", "LXXV", "LXXVI", "LXXVII", "LXXVIII", "LXXIX", "LXXX",
                "LXXXI", "LXXXII", "LXXXIII", "LXXXIV", "LXXXV", "LXXXVI", "LXXXVII", "LXXXVIII", "LXXXIX", "XC",
                "XCI", "XCII", "XCIII", "XCIV", "XCV", "XCVI", "XCVII", "XCVIII", "XCIX", "C"
        };
        final String rom = roman[numArabian];
        return rom;
    }
    /*private static void kos(){
        System.out.println("Некорректный ввод"); Про систем ексит нет в условии задачи
        System.ексит(0);
    }*/

    private static int romanToNumber (String roman) {
            if (roman.equals("I")) {
                return 1;
            } else if (roman.equals("II")) {
                return 2;
            } else if (roman.equals("III")) {
                return 3;
            } else if (roman.equals("IV")) {
                return 4;
            } else if (roman.equals("V")) {
                return 5;
            } else if (roman.equals("VI")) {
                return 6;
            } else if (roman.equals("VII")) {
                return 7;
            } else if (roman.equals("VIII")) {
                return 8;
            } else if (roman.equals("IX")) {
                return 9;
            } else if (roman.equals("X")) {
                return 10;
            }
        return -1;
    }

    public static int calc (int num1, int num2, char op) {
        int result = 0;
            switch (op) {
                case '+':
                    result = num1 + num2;
                    break;
                case '-':
                    result = num1 - num2;
                    break;
                case '*':
                    result = num1 * num2;
                    break;
                case '/':
                    result = num1 / num2;
                    break;
            }
            return result;
        }
    }
