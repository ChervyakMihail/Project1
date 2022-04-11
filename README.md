#include <iostream>
#include <string>
 
using namespace std;
 
int sumD1, sumD2;
int** square;
 
string Vvod(int size, int sumD1, int sumD2) {
    cout << "Введите размер стороны квадрата: ";
    cin >> size;
    square = new int* [size];
 
    cout << "Введите элементы массива:" << endl;
    for (int i = 0; i < size; i++) {
        square[i] = new int[size];
        for (int j = 0; j < size; j++) {
            cout << "(" << i << "," << j << ") = ";
            cin >> square[i][j];
            if (i == j) sumD1 += square[i][j];
            if (i == size - j - 1) sumD2 += square[i][j];
        }
    }
}
string Vyvod(int size) {
    cout << "Ваш квадрат:" << endl;
    for (int i = 0; i < size; i++) {
        for (int j = 0; j < size; j++) {
            cout << " " << square[i][j] << " ";
        }
    cout << endl;
    }
}
string Proverka( int size, int** squar, int tempSum1, int tempSum2, bool magicSquare = true) {
    if (sumD1 != sumD2) magicSquare = false;
    else {
        for (int i = 0; i < size; i++) {
            tempSum1 = 0;
            tempSum2 = 0;
            for (int j = 0; j < size; j++) {
                tempSum1 += square[i][j];
                tempSum2 += square[j][i];
            }
            if (tempSum1 != sumD1 || tempSum2 != sumD1) {
                magicSquare = false;
            }
        }
    }
    if (magicSquare = true) cout << "Это волшебный квадрат!" << endl;
    else cout << "Это не волшебный квадрат!" << endl;
}
 
int main() {
    setlocale(LC_ALL,"rus");
 
    Vvod(5, 0, 0);
    Vyvod(5);
    Proverka(5, 0, 0, 0);
 
    return 0;
}
