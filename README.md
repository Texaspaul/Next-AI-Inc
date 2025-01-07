/
package TexasNextAlInc;

public class NextAIInc {
    // Method to calculate and print total weekly pay for contractors
    public void calculatePay(int basePay, int hoursWorked) {
        // Define minimum base pay and maximum allowed hours
        final int MIN_BASE_PAY = 30000;
        final int MAX_HOURS = 72;

        // Check if base pay is below the minimum
        if (basePay < MIN_BASE_PAY) {
            System.out.println("Error: base pay must not be below UGX " + MIN_BASE_PAY);
            return;
        }

        // Check if hours worked exceeds the maximum
        if (hoursWorked > MAX_HOURS) {
            System.out.println("Error: hours worked must not exceed " + MAX_HOURS + " hours");
            return;
        }

        // Calculate pay
        int regularHours = Math.min(hoursWorked, 48); // regular hours capped at 48
        int overtimeHours = Math.max(0, hoursWorked - 48); // overtime hours are any hours over 48

        // Calculate total pay
        int totalPay = regularHours * basePay + (overtimeHours * basePay * 2);

        // Print total pay
        System.out.println("Total weekly pay: UGX " + totalPay);
    }

    public static void main(String[] args) {
        NextAIInc company = new NextAIInc();
        
        // Test case A
        System.out.println("Contractor A:");
        company.calculatePay(30000, 51); // expected: total pay includes 48 regular hours and 3 overtime hours
        
        // Test case B
        System.out.println("Contractor B:"); 
        company.calculatePay(20000, 40); // expected: error due to base pay below minimum
        
        // Test case C
        System.out.println("Contractor C:");
        company.calculatePay(35000, 96); // expected: error due to hours worked exceeding 72-hour limit
    }
}
