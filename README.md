# MemoryGame
A memory matching game.

import java.util.*;

class Main {
  public static void main(String[] args) 
  { 
    Scanner input = new Scanner(System.in);
    
    while(true)
    {
      System.out.println("****************");
      System.out.println("  WELCOME TO \nTHE MEMORY GAME");
      System.out.println("****************");
      System.out.println("Press n for new game or q to quit.");
      String play = input.nextLine();
      if(play.equals("n")) 
      {
        shuffle();
        
        // prints * place holders on gameboard
        for(int i = 0; i < 6; i++) 
        {
          for(int j = 0; j < 6; j++) 
          {
            gameboard[i][j] = " * ";
          }
        }
        printGameboard();
        checkInput(cards);
        break;
      } 
      else if (play.equals("q")) {
        System.out.println("Thank you for playing! \nEnding game now...");
        break;
      } 
      else 
      {
        System.out.println("Invalid choice. Try again.");
        continue;
      }
    }
  }

  // use a multidimensional arrays for rows & columns
  public static String [][] gameboard = new String[6][6];
  public static String [][] cards = new String [6][6];
  
  public static Scanner input = new Scanner(System.in);
  
  // method to display the gameboard
  public static void printGameboard()
    {
      for(int i = 0; i < 6; i++)
      {
        System.out.print("|");
        for(int j = 0; j < 6; j++)
        {
          System.out.print(gameboard[i][j]);
          System.out.print("|");
        }
        System.out.println();
      }
    }
 
  // method to shuffle images
  public static void shuffle()
  {
    Random shuffle = new Random();
    ArrayList<String> img = new ArrayList<String>(); // array list for img
    img.add("🦞");
    img.add("🐚");
    img.add("🐙");
    img.add("🦑");
    img.add("🦐");
    img.add("🐡");
    img.add("🐠");
    img.add("🐟");
    img.add("🐳");
    img.add("🦭");
    img.add("🐬");
    img.add("🦈");
    img.add("🦦");
    img.add("🦀");
    img.add("⛵");
    img.add("⚓");
    img.add("🧭");
    img.add("🐢");
    img.add("🦞");
    img.add("🐚");
    img.add("🐙");
    img.add("🦑");
    img.add("🦐");
    img.add("🐡");
    img.add("🐠");
    img.add("🐟");
    img.add("🐳");
    img.add("🦭");
    img.add("🐬");
    img.add("🦈");
    img.add("🦦");
    img.add("🦀");
    img.add("⛵");
    img.add("⚓");
    img.add("🧭");
    img.add("🐢");
    

    // randomizes images for cards
    int index;
    for (int i = 0; i < 6; i++)
    {
      for(int j = 0; j < 6; j++)
      {
        index = shuffle.nextInt(img.size());   //Tutoring help from Cherie
        cards[i][j] = img.get(index);
        img.remove(index);
      }
    }
  }

  // check user input for duplicate inputs and matched images
  // Tutoring help from Devin
  public static void checkInput(String [][] cards){
    while(true){
      if(!gameOver())
      {         
        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        System.out.println("Choose a Row: (1-6)");
        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        int row1 = input.nextInt();
        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        System.out.println("Choose a Column: (1-6)");
        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        int column1 = input.nextInt();

        if(!gameboard[row1-1][column1-1].equals(" * ")){
          System.out.println("Already Entered!");
          gameboard[row1-1][column1-1] = " * ";
          System.out.println();

          printGameboard();
          continue;  
        }
        else
        {
          gameboard[row1-1][column1-1] = " " + cards[row1-1][column1-1] + " ";
          printGameboard();
        }

        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        System.out.println("Choose a Row: (1-6)");
        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        int row2 = input.nextInt();
        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        System.out.println("Choose a Column: (1-6)");
        System.out.println("~~~~~~~~~~~~~~~~~~~~~~");
        int column2 = input.nextInt();

        if(!gameboard[row2-1][column2-1].equals(" * "))
        {
          System.out.println("Already Entered! Try again.");
          gameboard[row1-1][column1-1] = " * ";
          System.out.println();

          printGameboard();
          continue;  
        }
        else
        {
          gameboard[row2-1][column2-1] = " " + cards[row2-1][column2-1] + " ";

          if(gameboard[row1-1][column1-1].equals(gameboard[row2-1][column2-1]))
          {
            printGameboard();
            System.out.println("You made a match!");
          }
          else 
          {
            printGameboard();
            System.out.println("Not a match!");
            gameboard[row1-1][column1-1] = " * ";
            gameboard[row2-1][column2-1] = " * ";
            printGameboard();              
          }
        } 
          
      } 
      else 
      {
        System.out.println("Game Over!");
        break;
      }
    }
  }

  //checks for * on gameboard. when * are gone, all matches made & game done
  public static boolean gameOver()
  {
    for(int i = 0; i < 6; i++)
    {
      for(int j = 0; j < 6; j++) 
      {
        if(gameboard[i][j].equals(" * ")) 
        {
          return false;
        }
      }
    }
    return true;
  }

} 
