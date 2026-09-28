import java.util.Scanner;

public class TrackNGo {

public static void main(String[] args) {  

    Scanner sc = new Scanner(System.in);  

    String[] busNumber = {"101", "102", "103", "104"};  

    String[][] stops = {  
        {"Chennai", "Guindy", "Tambaram"},  
        {"Guindy", "Ambattur", "Avadi"},  
        {"T Nagar", "Guindy", "Tambaram"},  
        {"Koyambedu", "Vadapalani", "Velachery"}  
    };  

    int[] arrivalTime = {5, 10, 7, 12};  

    // 0 = Available, 1 = Occupied  
    int[][] seats = {  
        {1, 1, 0, 0, 0, 1, 0, 0, 1, 0},  
        {1, 0, 1, 1, 0, 0, 0, 1, 0, 0},  
        {1, 1, 1, 0, 0, 0, 1, 0, 0, 0},  
        {0, 1, 0, 1, 1, 0, 0, 0, 1, 0}  
    };  

    System.out.println("===== TRACK N GO =====");  

    System.out.print("Enter your bus stop: ");  
    String stop = sc.nextLine();  

    boolean found = false;  

    System.out.println("\nBuses coming to " + stop + ":");  

    for (int i = 0; i < busNumber.length; i++) {  

        boolean busFound = false;  

        for (int j = 0; j < stops[i].length; j++) {  

            if (stops[i][j].equalsIgnoreCase(stop)) {  
                busFound = true;  
                break;  
            }  
        }  

        if (busFound) {  

            found = true;  

            int occupied = 0;  

            for (int j = 0; j < 10; j++) {  
                if (seats[i][j] == 1) {  
                    occupied++;  
                }  
            }  

            System.out.println("\n----------------------");  
            System.out.println("Bus Number : " + busNumber[i]);  
            System.out.println("Arrives in : "  
                               + arrivalTime[i] + " minutes");  

            if (occupied <= 3) {  
                System.out.println("Crowd Status: GREEN");  
                System.out.println("Less Crowded");  
            }  
            else if (occupied <= 6) {  
                System.out.println("Crowd Status: YELLOW");  
                System.out.println("Moderately Crowded");  
            }  
            else {  
                System.out.println("Crowd Status: RED");  
                System.out.println("Highly Crowded");  
            }  
        }  
    }  

    if (!found) {  
        System.out.println("\nNo buses found at this stop.");  
    }  

    sc.close();  
}

}
