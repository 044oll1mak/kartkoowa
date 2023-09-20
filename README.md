pierwiastki tablica

    public class TablicaPierwiastki {
    public static void main(String[] args) {
        // Deklaracja tablicy na 10 liczb rzeczywistych
        double[] tablica = new double[10];
        
        // Wypełnienie tablicy pierwiastkami indeksów
        for (int i = 0; i < 10; i++) {
            tablica[i] = Math.sqrt(i);
        }
        
        // Wyświetlenie zawartości tablicy
        for (int i = 0; i < 10; i++) {
            System.out.println("tablica[" + i + "] = " + tablica[i]);
        }
    }
    }


ciagi fibonaciego

        public class FibonacciArray {
        public static void main(String[] args) {
        int n = 40; // liczba elementów w tablicy
        long[] fibonacciArray = new long[n]; // deklaracja tablicy

        // Pierwsze dwie liczby Fibonacciego
        fibonacciArray[0] = 0;
        fibonacciArray[1] = 1;

        // Obliczanie kolejnych liczb Fibonacciego i wstawianie ich do tablicy
        for (int i = 2; i < n; i++) {
            fibonacciArray[i] = fibonacciArray[i - 1] + fibonacciArray[i - 2];
        }

        // Wyświetlenie zawartości tablicy
        for (int i = 0; i < n; i++) {
            System.out.println("Fibonacci[" + i + "] = " + fibonacciArray[i]);
        }
    }
    }


sito erastotenesa

    public class SitoEratostenesa {
    public static void main(String[] args) {
        int n = 1000;
        boolean[] primes = new boolean[n + 1];

        // Inicjalizacja sita - zakładamy, że wszystkie liczby są pierwsze na początek
        for (int i = 2; i <= n; i++) {
            primes[i] = true;
        }

        // Sito Eratostenesa
        for (int p = 2; p * p <= n; p++) {
            if (primes[p]) {
                for (int i = p * p; i <= n; i += p) {
                    primes[i] = false;
                }
            }
        }

        // Wypisanie liczb pierwszych mniejszych od 1000
        System.out.println("Liczby pierwsze mniejsze od 1000:");
        for (int i = 2; i < 1000; i++) {
            if (primes[i]) {
                System.out.print(i + " ");
            }
        }
        System.out.println();

        // Wypisanie liczb pierwszych z zakresu od x do y
        int x = 100; // Zakres początkowy (x)
        int y = 500; // Zakres końcowy (y)
        System.out.println("Liczby pierwsze z zakresu od " + x + " do " + y + ":");
        for (int i = x; i <= y; i++) {
            if (i < 1000 && primes[i]) {
                System.out.print(i + " ");
            }
        }
    }
    }

    public class Main {
    public static void main(String[] args) {
        for (int i = 10; i <= 99; i += 2) {
            System.out.print(i + " ");
        }
    }
    }



liczba paliodrom

    public class NajblizszaPalindromiczna {
    public static boolean isPalindromic(int number) {
        String numStr = String.valueOf(number);
        String reversedNumStr = new StringBuilder(numStr).reverse().toString();
        return numStr.equals(reversedNumStr);
    }

    public static int znajdzNajblizszaPalindromiczna(int liczba) {
        int mniejsza = liczba - 1;
        int wieksza = liczba + 1;

        while (true) {
            if (isPalindromic(mniejsza)) {
                return mniejsza;
            } else if (isPalindromic(wieksza)) {
                return wieksza;
            }

            mniejsza--;
            wieksza++;
        }
    }

    public static void main(String[] args) {
        int liczba = 1015;
        int najblizszaPalindromiczna = znajdzNajblizszaPalindromiczna(liczba);
        System.out.println("Najbliższa liczba palindromiczna dla " + liczba + " to " + najblizszaPalindromiczna);
    }
    }


czy anagram

    import java.util.Arrays;
    import java.util.Scanner;
    public class AnagramChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Wczytaj pierwszy ciąg znaków
        System.out.print("Podaj pierwszy ciąg znaków: ");
        String pierwszyCiąg = scanner.nextLine();

        // Wczytaj drugi ciąg znaków
        System.out.print("Podaj drugi ciąg znaków: ");
        String drugiCiąg = scanner.nextLine();

        // Usuń białe znaki i zamień na małe litery
        pierwszyCiąg = pierwszyCiąg.replaceAll("\\s", "").toLowerCase();
        drugiCiąg = drugiCiąg.replaceAll("\\s", "").toLowerCase();

        // Sprawdź, czy ciągi znaków są anagramami
        if (czyAnagram(pierwszyCiąg, drugiCiąg)) {
            System.out.println("Podane ciągi znaków są anagramami.");
        } else {
            System.out.println("Podane ciągi znaków nie są anagramami.");
        }
    }

    // Funkcja sprawdzająca, czy ciągi znaków są anagramami
    public static boolean czyAnagram(String s1, String s2) {
        // Jeśli długości ciągów są różne, to na pewno nie są anagramami
        if (s1.length() != s2.length()) {
            return false;
        }

        // Konwertuj ciągi znaków na tablice znaków
        char[] charArray1 = s1.toCharArray();
        char[] charArray2 = s2.toCharArray();

        // Posortuj tablice znaków
        Arrays.sort(charArray1);
        Arrays.sort(charArray2);

        // Porównaj posortowane tablice znaków
        return Arrays.equals(charArray1, charArray2);
    }
    }


czy liczba jest pierwsza   
    
    public class CzyLiczbaPierwsza {
    public static boolean czyLiczbaPierwsza(int liczba) {
        if (liczba <= 1) {
            return false;
        }
        
        if (liczba <= 3) {
            return true;
        }
        
        if (liczba % 2 == 0 || liczba % 3 == 0) {
            return false;
        }
        
        int i = 5;
        while (i * i <= liczba) {
            if (liczba % i == 0 || liczba % (i + 2) == 0) {
                return false;
            }
            i += 6;
        }
        
        return true;
    }

    public static void main(String[] args) {
        int liczba = 17; // Zmienić na dowolną liczbę, którą chcesz sprawdzić
        if (czyLiczbaPierwsza(liczba)) {
            System.out.println(liczba + " jest liczbą pierwszą.");
        } else {
            System.out.println(liczba + " nie jest liczbą pierwszą.");
        }
    }
    }

