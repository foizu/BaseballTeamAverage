# BaseballTeamAverage
This is just a program I created for a HW assignment in my CSC1115 Intro to Java Class. I use this for good practice.

public static void main(String[] args) {


        //Create a scanner object for input
        Scanner input = new Scanner(System.in);

        //declare variables to store team stats
        /*teamID - teams identification number
          wins  - number of team wins
          losses - number of losses
          cancelled - games cancelled
          totalGames - number of games in season
         */

        int teamID, wins, losses, cancelled, totalGames;

        //variable that Counts the number of teams processed.
        int totalTeams = 0;

        //track the best non-1 winning average

        //Store the best winning average
        double bestWinningAvg = 0;
        int bestTeamID = 0;

        //loop to process multiple teams
        // repeatedly ask for and process data for each team. The loop will continue until the user inputs -1 as the team ID, which wil stop the program

        while (true) {

            //Prompt user to enter a team ID
            System.out.print("Enter team ID (or -1 to stop: ");

            //reads the team ID entered by the user and stores it in team ID variable
            teamID = input.nextInt();

            //if the user enters -1, the loop breaks, and the program will stop asking fro new team data.
            if (teamID == -1) break;

            //Prompt user to enter the number of wins for the current team
            System.out.print("Enter number of wins: ");
            //Read number of wins entered and store it in wins variable.
            wins = input.nextInt();

            //Prompt user to enter number of losses for current team
            System.out.print("Enter number of losses: ");
            //Read number of losses entered and store it in losses variable.
            losses = input.nextInt();

            //Prompt user to enter number of cancelled games for current team.
            System.out.print("Enter number of cancelled games: ");
            //Read number of cancelled games entered and store it in cancelled variable.
            cancelled = input.nextInt();

            //Prompt user to enter total games in season for current team
            System.out.print("Enter total games in season: ");
            //Read number of total games entered and store it in totalGames variable.
            totalGames = input.nextInt();


            //Declare gamesPlayed variable and calculate the number of games won and loss add them together and that is the value of gamesPlayed
            int gamesPlayed = wins + losses;
            //Declare gamesRemaining variable and calculate total games played subtracted from (games played and games cancelled).
            int gamesRemaining = totalGames - (gamesPlayed + cancelled);

            //Print the team ID, Print the wins, losses, and cancelled games.
            System.out.println("Team: " + teamID + "  " + " wins " + wins +  losses + " losses " + cancelled + " cancelled ");
            //Print the number of total games played
            System.out.println("Total games played " + gamesPlayed);
            //Print the number of games remaining
            System.out.println("Games remaining: " + gamesRemaining);

            //Create if loop:
            // if the total number of games played equals to the total number of games then season is finished.
            if (gamesPlayed + cancelled == totalGames) {
                System.out.println(" The season is finished. ");



            } else {

                System.out.println(gamesRemaining + "games remaining. ");
            }

            //Calculate the winning average by dividing wins by the number of games played. The result is cast to double for decimal
            double winningAverage = (double) wins / gamesPlayed;
            //Print the winning average rounded to four decimals
            System.out.printf("Winning average: %.4fn" , winningAverage);

            //create another if loop:
            //Compare games remaining with games won
            if (gamesRemaining >= wins) {
                //if remaining games surpasses or equals to the number of wins then print message.
                System.out.println("Number of games remaining is greater than or equal to number won. ");

            } else {
                //else if number of remaining games is not enough, then print this message
                System.out.println("Number of games remaining is greater than number lost. ");
            }

            //Calculate the maximum possible wins if th team wins all remaining games.
            int maxWins = wins + gamesRemaining;
            //Calculate the maximum winning average if the team wins all remaining games.
            double maxWinningAverage = (double) maxWins / totalGames;
            //Print the winning record and average if the team wins all remaining games.
            System.out.printf("If team wins all remaining games: %d-%d, Winning average: %.4f%n", maxWins, losses, maxWinningAverage);

            //if the curent team's winning average is better than the previously stored best winning average and is not a perfect 1.000, update the best winnning avergae and the team ID.
            if (winningAverage > bestWinningAvg && winningAverage < 1) {
                bestWinningAvg = winningAverage;
                bestTeamID = teamID;
            }
            //Increment the totalTeams counter for each team processed.
            totalTeams++;
            //Add a blank line between
            System.out.println();
        }

        //Print total number of teams processed.
        System.out.println("Total number of teams processed: " + totalTeams);

        //Team with best winning average has been found, print its team ID and winning average.
        if (bestTeamID != 0) {
            System.out.printf(" Team with best winning average (not 1.000): Team %d with %.4f%n", bestTeamID, bestWinningAvg);
        }


    }


}
