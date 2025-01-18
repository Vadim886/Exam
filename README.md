//Решение неверное, но скинул что успел решить

//Пусть n>9 красных и n синих точек на плоскости заданы своими координатами. 
// Построить n отрезков с разными концами, суммарная длина которых минимальна 
// (каждая точка является концом только одного отрезка).

#include <iostream>

using namespace std;

int main() {
	const int n = 10;
	double red[n][2] = {{0,0},{1,1},{2,2},{3,3},{4,4},{5,5},{6,6},{7,7},{8,8},{9,9}};
	double blue[n][2] = {{1,3},{3,2},{0,2},{2,0},{0,3},{3,0},{0,4},{4,0},{0,5},{5,0}};

	double length = 0;
	bool used[n] = {false}; //Отслеживание использованных синих точек

	for (int i = 0; i < n; i++) {
		double minDistance = 100000;
		int minIndex = -1; // Индекс минимальной синей точки

		for (int j = 0; j < n; j++) {
			if (!used[j]) {
				double dx = red[i][0] - blue[j][0];
				double dy = red[i][1] - blue[j][1];
				double distance = dx * dx + dy * dy;

				if (distance < minDistance) {
					minDistance = distance;
					minIndex = j;
				}
			}
		}
		if (minIndex != -1) {
			used[minIndex] = true;// Точка использована
			length += minDistance;
		}
	}
	cout << "Min distance: " << length << endl;

	return 0;
}

![Снимок экрана 2025-01-18 125351](https://github.com/user-attachments/assets/ccfa6ab0-5460-4413-a166-c6a46e552b87)


