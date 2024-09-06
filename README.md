# Task-3
class Student:
    def __init__(self, name):
        self.name = name
        self.grades = {}

   def add_grade(self, subject, grade):
        if subject in self.grades:
            self.grades[subject].append(grade)
        else:
            self.grades[subject] = [grade]

   def calculate_average(self):
        total_grades = 0
        total_subjects = 0
        for grades in self.grades.values():
            total_grades += sum(grades)
            total_subjects += len(grades)
        if total_subjects == 0:
            return 0
        return total_grades / total_subjects

   def get_letter_grade(self, average):
        if average >= 90:
            return "A"
        elif average >= 80:
            return "B"
        elif average >= 70:
            return "C"
        elif average >= 60:
            return "D"
        else:
            return "F"

   def display_overall_grade(self):
        average = self.calculate_average()
        letter_grade = self.get_letter_grade(average)
        print(f"Student Name: {self.name}")
        print(f"Average Grade: {average:.2f}")
        print(f"Letter Grade: {letter_grade}")

# Main program
def main():
    student_name = input("Enter the student's name: ")
    student = Student(student_name)
    
   while True:
        print("\nOptions:")
        print("1. Add Grade")
        print("2. Display Overall Grade")
        print("3. Exit")
        
  choice = input("Choose an option: ")
        
  if choice == "1":
            subject = input("Enter the subject: ")
            grade = float(input("Enter the grade: "))
            student.add_grade(subject, grade)
        elif choice == "2":
            student.display_overall_grade()
        elif choice == "3":
            print("Exiting the program.")
            break
        else:
            print("Invalid option. Please try again.")

if __name__ == "__main__":
    main()
