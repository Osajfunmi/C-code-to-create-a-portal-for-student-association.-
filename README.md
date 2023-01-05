# C-code-to-create-a-portal-for-student-association.-

#include <iostream>
#include <string>
#include <unordered_map>

struct Student {
  std::string name;
  std::string email;
  std::string association;
};

int main() {
  // Create a map to store the registered students
  std::unordered_map<std::string, Student> students;

  while (true) {
    std::cout << "Enter 'r' to register, 'l' to login, or 'q' to quit: ";
    char input;
    std::cin >> input;

    if (input == 'q') {
      break;
    } else if (input == 'r') {
      // Prompt the user for information about a student
      Student student;

      std::cout << "Enter name for student: ";
      std::cin.ignore();
      std::getline(std::cin, student.name);

      std::cout << "Enter email for student: ";
      std::getline(std::cin, student.email);

      std::cout << "Enter association for student: ";
      std::getline(std::cin, student.association);

      // Store the student in the map using their email as the key
      students[student.email] = student;
      std::cout << "Successfully registered student " << student.name << " with email " << student.email << std::endl;
    } else if (input == 'l') {
      // Prompt the user for their email
      std::string email;
      std::cout << "Enter email: ";
      std::cin.ignore();
      std::getline(std::cin, email);

      // Look up the student in the map
      auto it = students.find(email);
      if (it != students.end()) {
        // Student was found, print their information
        std::cout << "Student " << it->second.name << " is logged in." << std::endl;
      } else {
        // Student was not found
        std::cout << "No student with email " << email << " was found." << std::endl;
      }
    }
  }

  return 0;
}
