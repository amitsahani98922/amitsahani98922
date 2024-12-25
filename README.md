# Initialize an empty dictionary to store student records
students = {}

def add_student(student_id, marks):
    """Add a new student record."""
    if student_id in students:
        print("Student ID already exists.")
    else:
        students[student_id] = marks
        print("Student record added successfully.")

def update_student(student_id, marks):
    """Update an existing student record."""
    if student_id in students:
        students[student_id] = marks
        print("Student record updated successfully.")
    else:
        print("Student ID not found.")

def delete_student(student_id):
    """Delete a student record."""
    if student_id in students:
        del students[student_id]
        print("Student record deleted successfully.")
    else:
        print("Student ID not found.")

def calculate_total_and_percentage():
    """Calculate total marks and percentage for each student."""
    results = {}
    for student_id, marks in students.items():
        total_marks = sum(marks.values())
        percentage = total_marks / len(marks)  # Assuming each subject has a weight of 100
        results[student_id] = {
            "total": total_marks,
            "percentage": percentage
        }
    return results

def display_rank():
    """Display students' ranks based on total marks."""
    results = calculate_total_and_percentage()
    ranked_students = sorted(results.items(), key=lambda x: x[1]['total'], reverse=True)

    print("\nStudent Ranks:")
    for rank, (student_id, data) in enumerate(ranked_students, start=1):
        print(f"Rank {rank}: Student ID {student_id} | Total Marks: {data['total']} | Percentage: {data['percentage']:.2f}%")

# Example usage
while True:
    print("\nStudent Records System")
    print("1. Add Student")
    print("2. Update Student")
    print("3. Delete Student")
    print("4. Display Ranks")
    print("5. Exit")

    choice = input("Enter your choice: ")
    if choice == "1":
        student_id = input("Enter Student ID: ")
        subjects = int(input("Enter number of subjects: "))
        marks = {}
        for _ in range(subjects):
            subject = input("Enter subject name: ")
            mark = int(input(f"Enter marks for {subject}: "))
            marks[subject] = mark
        add_student(student_id, marks)
    elif choice == "2":
        student_id = input("Enter Student ID: ")
        subjects = int(input("Enter number of subjects: "))
        marks = {}
        for _ in range(subjects):
            subject = input("Enter subject name: ")
            mark = int(input(f"Enter marks for {subject}: "))
            marks[subject] = mark
        update_student(student_id, marks)
    elif choice == "3":
        student_id = input("Enter Student ID: ")
        delete_student(student_id)
    elif choice == "4":
        display_rank()
    elif choice == "5":
        print("Exiting...")
        break
    else:
        print("Invalid choice. Please try again.")
