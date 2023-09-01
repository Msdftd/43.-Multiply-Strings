# 43.-Multiply-Strings
43. Multiply Strings Leetcode Solution

class Solution {
    public String multiply(String num1, String num2) {
        int len1 = num1.length();
        int len2 = num2.length();
        int[] result = new int[len1 + len2];

        // Convert the characters to integers and perform multiplication
        for (int i = len1 - 1; i >= 0; i--) {
            int digit1 = num1.charAt(i) - '0';

            for (int j = len2 - 1; j >= 0; j--) {
                int digit2 = num2.charAt(j) - '0';
                int product = digit1 * digit2;

                // Add the product to the appropriate position in the result array
                int sum = result[i + j + 1] + product;
                result[i + j + 1] = sum % 10;
                result[i + j] += sum / 10;
            }
        }

        // Convert the result array to a string
        StringBuilder sb = new StringBuilder();
        for (int digit : result) {
            if (!(sb.length() == 0 && digit == 0)) {
                sb.append(digit);
            }
        }

        // Handle the case where the result is "0"
        return sb.length() == 0 ? "0" : sb.toString();
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        // Example usage:
        String num1 = "123";
        String num2 = "456";
        String output = solution.multiply(num1, num2);
        System.out.println(output);  // Output: "56088"
        
    }
}
