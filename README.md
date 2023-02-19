# Task2
Programm that sum up to 13
import java.util.*;

public class Task2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read input list of integers
        List<Integer> inputList = new ArrayList<Integer>();
        String[] inputString = scanner.nextLine().split(" ");
        for (int i = 0; i < inputString.length; i++) {
            inputList.add(Integer.parseInt(inputString[i]));
        }

        // Find all pairs of integers that sum up to 13
        List<List<Integer>> sumPairs = new ArrayList<List<Integer>>();
        for (int i = 0; i < inputList.size(); i++) {
            int num1 = inputList.get(i);
            for (int j = i + 1; j < inputList.size(); j++) {
                int num2 = inputList.get(j);
                if (num1 + num2 == 13) {
                    List<Integer> pair = new ArrayList<Integer>();
                    pair.add(Math.min(num1, num2));
                    pair.add(Math.max(num1, num2));
                    sumPairs.add(pair);
                }
            }
        }

        // Sort pairs in ascending order and print output
        Collections.sort(sumPairs, new Comparator<List<Integer>>() {
            @Override
            public int compare(List<Integer> list1, List<Integer> list2) {
                int num1a = list1.get(0);
                int num1b = list1.get(1);
                int num2a = list2.get(0);
                int num2b = list2.get(1);
                if (num1a != num2a) {
                    return Integer.compare(num1a, num2a);
                } else {
                    return Integer.compare(num1b, num2b);
                }
            }
        });
        for (List<Integer> pair : sumPairs) {
            System.out.println(pair.get(0) + " " + pair.get(1));
        }
    }
}
