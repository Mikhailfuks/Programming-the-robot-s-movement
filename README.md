#include <iostream>
#include <cmath>

using namespace std;

// Класс для моделирования робота
class Robot {
private:
    double x, y; // Координаты робота
    double angle; // Угол ориентации робота (в радианах)

public:
    // Конструктор
    Robot(double initialX, double initialY, double initialAngle) : x(initialX), y(initialY), angle(initialAngle) {}

    // Методы для получения координат и угла
    double getX() const { return x; }
    double getY() const { return y; }
    double getAngle() const { return angle; }

    // Метод для поворота робота
    void rotate(double deltaAngle) {
        angle += deltaAngle;
        // Нормализация угла в диапазон от 0 до 2π
        angle = fmod(angle, 2 * M_PI);
    }

    // Метод для движения робота вперед
    void moveForward(double distance) {
        x += distance * cos(angle);
        y += distance * sin(angle);
    }

    // Метод для вывода координат робота
    void printPosition() const {
        cout << "Координаты: (" << x << ", " << y << ")" << endl;
        cout << "Угол: " << angle << " (радианы)" << endl;
    }
};

int main() {
    // Создание робота с начальными координатами (0, 0) и углом 0 радиан
    Robot myRobot(0, 0, 0);

    // Движение робота вперед на 5 единиц
    myRobot.moveForward(5);

    // Поворот робота на 90 градусов (π/2 радиан)
    myRobot.rotate(M_PI / 2);

    // Движение робота вперед на 3 единицы
    myRobot.moveForward(3);

    // Вывод текущего положения робота
    myRobot.printPosition();

    return 0;
}
