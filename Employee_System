class Employee:
    def __init__(self, name, age, salary):
        if age <= 0:
            raise ValueError("Age must be positive")

        if salary < 0:
            raise ValueError("Salary cannot be negative")

        self.name = name
        self.age = age
        self.salary = salary

    def __str__(self):
        return f"Name: {self.name}, Age: {self.age}, Salary: ₹{self.salary:,}"


class EmployeesManager:
    def __init__(self):
        self.employees = []

    def add_employee(self, employee):
        self.employees.append(employee)

    def list_employees(self):
        if not self.employees:
            print("No employees found")
            return

        for emp in self.employees:
            print(emp)

    def find_employee(self, name):
        for emp in self.employees:
            if emp.name.lower() == name.lower():
                return emp
        return None

    def update_salary(self, name, new_salary):
        if new_salary < 0:
            print("Invalid salary")
            return

        emp = self.find_employee(name)

        if emp:
            emp.salary = new_salary
            print("Salary updated")
        else:
            print("Employee not found")

    def delete_by_age_range(self, min_age, max_age):
        before_count = len(self.employees)

        self.employees = [
            emp for emp in self.employees
            if not (min_age <= emp.age <= max_age)
        ]

        after_count = len(self.employees)
        print(f"{before_count - after_count} employee(s) deleted")


class FrontendManager:
    def __init__(self):
        self.manager = EmployeesManager()

    def menu(self):
        while True:
            print("\n1. Add Employee")
            print("2. List Employees")
            print("3. Find Employee")
            print("4. Update Salary")
            print("5. Delete by Age Range")
            print("6. Exit")

            choice = input("Enter choice: ")

            if choice == "1":
                name = input("Enter name: ")

                try:
                    age = int(input("Enter age: "))
                    salary = int(input("Enter salary: "))
                except ValueError:
                    print("Invalid input. Please enter numbers only.")
                    continue

                try:
                    emp = Employee(name, age, salary)
                    self.manager.add_employee(emp)
                    print("Employee added successfully")
                except ValueError as e:
                    print(e)

            elif choice == "2":
                self.manager.list_employees()

            elif choice == "3":
                name = input("Enter name: ")
                result = self.manager.find_employee(name)

                if result:
                    print("Found:", result)
                else:
                    print("Employee not found")

            elif choice == "4":
                name = input("Enter name: ")

                try:
                    salary = int(input("Enter new salary: "))
                except ValueError:
                    print("Invalid salary input")
                    continue

                self.manager.update_salary(name, salary)

            elif choice == "5":
                try:
                    min_age = int(input("Enter min age: "))
                    max_age = int(input("Enter max age: "))
                except ValueError:
                    print("Invalid age input")
                    continue

                self.manager.delete_by_age_range(min_age, max_age)

            elif choice == "6":
                print("Exiting...")
                break

            else:
                print("Invalid choice")


if __name__ == "__main__":
    app = FrontendManager()
    app.menu()