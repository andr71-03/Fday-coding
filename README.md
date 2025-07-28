#include <iostream>
#include <iomanip>
using namespace std;

#define RESET   "\033[0m"
#define RED     "\033[31m"
#define GREEN   "\033[32m"
#define WHITE   "\033[37m"

int main() {
    string pNames[5] = {"LeBron James","Dorian Finney-Smith","Jaxson Hayes","Luka Doncic","Austin Reaves"};
    string pNum[5] = {"23","17","11","77","15"};
    string pPos[5] = {"Forward","Forward","Center","Guard","Guard"};

    int pnts[5] = {17, 3, 19, 25, 30};
    int asts[5] = {12, 2, 1, 8, 3};
    int rebs[5] = {5, 4, 8, 10, 1};

    // Sort players by points (descending)
    for (int z = 0; z < 4; z++) {
        for (int i = 0; i < 4; i++) {
            if (pnts[i] < pnts[i + 1]) {
                swap(pnts[i], pnts[i + 1]);
                swap(asts[i], asts[i + 1]);
                swap(rebs[i], rebs[i + 1]);
                swap(pNames[i], pNames[i + 1]);
                swap(pNum[i], pNum[i + 1]);
                swap(pPos[i], pPos[i + 1]);
            }
        }
    }

    cout << setw(20) << left << "Name"
         << setw(10) << left << "Position"
         << setw(6)  << left << "Pnts"
         << setw(6)  << left << "Asts"
         << setw(6)  << left << "Rebs" << endl;

    for (int j = 0; j < 5; j++) {
        string color;
        if (j == 0)
            color = GREEN;  // Top scorer
        else if (j == 4)
            color = RED;    // Lowest scorer
        else
            color = WHITE;

        cout << color;
        cout << setw(20) << left << pNames[j]
             << setw(10) << left << pPos[j]
             << setw(6)  << left << pnts[j]
             << setw(6)  << left << asts[j]
             << setw(6)  << left << rebs[j] << endl;
        cout << RESET;
    }

    return 0;
}
