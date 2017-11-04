# Samples
 import java.util.Scanner;

public class Main {
    public static void main(String args[]) {
        
         String inputvalue;
        int x,y;
        int d;
        char dir1;
        String dir, p;
        //Taking input from user
        Scanner in = new Scanner(System.in);
        inputvalue = in.nextLine();
        //Splitting the arguments based on space and storing in variables
        String[] value = inputvalue.split(" ");
        x = Integer.parseInt(value[0]);
        y = Integer.parseInt(value[1]);
        dir = value[2];
        p = value[3];
        //Stroring the path in char array
        char[] path = p.toCharArray();
        //Assigning a number to each direction
        if(dir.equals("North") || dir.equals("north")){
            dir1 = 'N';
            d = 0;
        }
        else if(dir.equals("East") || dir.equals("east")){
            dir1 = 'E';
            d = 1;
        }
        else if(dir.equals("South") || dir.equals("south")){
            dir1 = 'S';
            d = 2;
        }
        else{
            dir1 = 'W';
            d = 3;
        }
        
       
        for(int i=0; i < path.length; i++){
            char move = path[i];
            //finding current direction based on move
            if (move == 'R'){
                d = (d + 1)%4;
            }
            else if (move == 'L'){
                d = (4 + d - 1)%4;
            }
            
            //Changing X and Y based on direction
            else if(move == 'W'){
                i++;
                int num = Character.getNumericValue(path[i]);
                if (d == 0){
                    y = y+num;
                }
                else if (d == 1){
                    x = x+num;
                }
                else if (d == 2){
                    y = y - num;
                }
                else{ // dir == W
                    x = x - num;
                }
            }
            else{
                i++;
            }
        }
        if(d == 0){
            dir = "North";
        }
        else if(d == 1){
            dir = "East";
        }
        if(d == 2){
            dir = "South";
        }
        if(d == 3){
            dir = "West";
        }
        System.out.println(x+" "+y+" "+dir);
        
    }
}
