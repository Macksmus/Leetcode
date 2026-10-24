```c
//Leetcode Problem 2409 - Count Days Spent Together. https://leetcode.com/problems/count-days-spent-together/description/?envType=daily-question&envId=2026-10-24
//This Program will find the overlap between two people's (Alice and Bob's) Days in a vacation, given the vacation is entered in MM-DD. 
int totalDays(char* x){ //need total amount of days, as we can assume all days are in same calender year
        int daysInMonth[] = {0, 31, 59, 90, 120, 151, 181, 212, 243, 273, 304, 334, 365}; //365 isn't really necessary here, but it's good to check that I every month together correctly
        int month = 10*(x[0] - '0') + x[1] - '0'; //learned that subtracting two chars gives the distance between the ASCII values of the char, so in this case if the value of x[0] = '9', x[0] - '0' = 9 (the integer)
        int day = 10*(x[3] - '0') + x[4] - '0';
        return (daysInMonth[month-1] + day);
}
int countDaysTogether(char* arriveAlice, char* leaveAlice, char* arriveBob, char* leaveBob) {
    int counter = 0;
    int arriveAliceNew = totalDays(arriveAlice);
    int leaveAliceNew = totalDays(leaveAlice);
    int arriveBobNew = totalDays(arriveBob);
    int leaveBobNew = totalDays(leaveBob);
    for(int i = 0; i <= 365; i++){
        if(arriveAliceNew <= i && i <= leaveAliceNew && arriveBobNew <= i && i <= leaveBobNew){ //Checking if the day in question (integer i) is in between the day of alice getting there and leaving and also in between the day bob got there and left. (essentially saying arrival <= i <= departure for both and if both are true, add one day that they were both there.)
            counter++;
        }
    }
    return counter;
}



```
