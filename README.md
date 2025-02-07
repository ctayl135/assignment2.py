# Program Name: Assignment2.py
# Course: IT3883/Section XXX
# Student Name: John Doe
# Assignment Number: Lab#
# Due Date: xx/xx/20XX
# Purpose: This program reads student names and their scores from an input file,
# calculates the final average for each student, and prints the results
# sorted in descending order based on their final average.
# List Specific resources used to complete the assignment: None (Self-Written)

# Function to read data from the input file
def read_student_data(filename):
    student_scores = []  # List to store student names and their calculated averages
    
    with open(filename, 'r') as file:
        for line in file:
            data = line.split()  # Split each line by spaces
            name = data[0]  # Extract the student name
            scores = list(map(int, data[1:]))  # Convert score values to integers
            avg_score = sum(scores) / len(scores)  # Calculate the average score
            student_scores.append((name, round(avg_score, 2)))  # Store name and rounded average
    
    return student_scores

# Function to sort and display students by their average scores
def display_sorted_results(student_scores):
    # Sort by average score in descending order
    sorted_students = sorted(student_scores, key=lambda x: x[1], reverse=True)
    
    # Print the results
    for student in sorted_students:
        print(f"{student[0]} {student[1]:.2f}")

# Main execution block
def main():
    input_filename = "students.txt"  # Change filename if needed
    student_scores = read_student_data(input_filename)  # Read student data
    display_sorted_results(student_scores)  # Sort and print results

# Run the program
if __name__ == "__main__":
    main()
