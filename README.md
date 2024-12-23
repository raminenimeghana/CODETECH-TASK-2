# CODETECH-TASK-2
Here is a simple Python program to track and calculate student grades:

# Student Grade Tracker

def calculate_grade(average):
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

def main():
    print("Welcome to the Student Grade Tracker!")
    student_grades = {}

    while True:
        print("\nMenu:")
        print("1. Add a student and grades")
        print("2. View all students and grades")
        print("3. Calculate average and final grade for a student")
        print("4. Exit")

        choice = input("Enter your choice (1/2/3/4): ")

        if choice == '1':
            name = input("Enter the student's name: ").strip()
            grades = input("Enter the student's grades separated by commas: ")
            try:
                grades = [float(grade) for grade in grades.split(",")]
                student_grades[name] = grades
                print(f"Grades for {name} added successfully.")
            except ValueError:
                print("Invalid grades format. Please enter numeric values separated by commas.")

        elif choice == '2':
            if not student_grades:
                print("No student data available.")
            else:
                for name, grades in student_grades.items():
                    print(f"{name}: Grades: {grades}")

        elif choice == '3':
            name = input("Enter the student's name: ").strip()
            if name in student_grades:
                grades = student_grades[name]
                average = sum(grades) / len(grades)
                grade = calculate_grade(average)
                print(f"{name} - Average: {average:.2f}, Final Grade: {grade}")
            else:
                print(f"No grades found for {name}.")

        elif choice == '4':
            print("Exiting the program. Goodbye!")
            break

        else:
            print("Invalid choice. Please select a valid option.")

# Run the program
main()
