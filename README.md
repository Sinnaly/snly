# snly
#include <iostream>
#include <string>

class Student {
private:
    std::string studentId;
    char sex;           // 'M' for male, 'F' for female
    char grade;         // 'A', 'B', 'C', 'D', 'F'

public:
    // Constructor
    Student(std::string id, char s, char g) {
        studentId = id;
        sex = s;
        grade = g;
    }

    // Setters
    void setStudentId(std::string id) { studentId = id; }
    void setSex(char s) { sex = s; }
    void setGrade(char g) { grade = g; }

    // Getters
    std::string getStudentId() const { return studentId; }
    char getSex() const { return sex; }
    char getGrade() const { return grade; }

    // Display student information
    void displayInfo() const {
        std::cout << "\nStudent Information:" << std::endl;
        std::cout << "ID: " << studentId << std::endl;
        std::cout << "Sex: " << sex << std::endl;
        std::cout << "Grade: " << grade << std::endl;
    }
};

int main() {
    std::string id;
    char sex, grade;
    int numStudents;

    std::cout << "Enter number of students: ";
    std::cin >> numStudents;

    // Dynamic array to store students
    Student* students[100];  // Assuming maximum 100 students

    // Input student information
    for(int i = 0; i < numStudents; i++) {
        std::cout << "\nEnter details for student " << (i+1) << ":" << std::endl;
        
        std::cout << "Enter Student ID: ";
        std::cin >> id;

        do {
            std::cout << "Enter Sex (M/F): ";
            std::cin >> sex;
            sex = toupper(sex);
        } while(sex != 'M' && sex != 'F');

        do {
            std::cout << "Enter Grade (A/B/C/D/F): ";
            std::cin >> grade;
            grade = toupper(grade);
        } while(grade != 'A' && grade != 'B' && grade != 'C' && grade != 'D' && grade != 'F');

        students[i] = new Student(id, sex, grade);
    }

    // Display all students
    std::cout << "\n====== Student Records ======" << std::endl;
    for(int i = 0; i < numStudents; i++) {
        students[i]->displayInfo();
    }

    // Clean up memory
    for(int i = 0; i < numStudents; i++) {
        delete students[i];
    }

    return 0;
}
