You can see the code below:

    #include <iostream>
    #include <vector>
    class CalcuClass {
    public:
        int Summation(const std::vector<int>& numbers) {
            int sum = 0;
            for (int num : numbers) {
                sum += num;
            }
            return sum;
        }
    
        int Multiply(const std::vector<int>& numbers) {
            int product = 1;
            for (int num : numbers) {
                product *= num;
            }
            return product;
        }
    
        double Division(const std::vector<int>& numbers) {
            if (numbers.size() < 2) {
                std::cerr << "Need at least two numbers for division." << std::endl;
                return 0;
            }
            double result = static_cast<double>(numbers[0]);
            for (size_t i = 1; i < numbers.size(); ++i) {
                if (numbers[i] == 0) {
                    std::cerr << "Division by zero is not allowed." << std::endl;
                    return 0;
                }
                result /= numbers[i];
            }
            return result;
        }
    
        int Subtract(const std::vector<int>& numbers) {
            if (numbers.empty()) {
                std::cerr << "No numbers to subtract." << std::endl;
                return 0;
            }
            int result = numbers[0];
            for (size_t i = 1; i < numbers.size(); ++i) {
                result -= numbers[i];
            }
            return result;
        }
    };
    
    void displayMenu() {
        std::cout << "===========================================" << std::endl;
        std::cout << "===============By (Batuhan Ozcil)==============" << std::endl;
        std::cout << "~~ WELCOME to Data Structure Algorithms program ~~" << std::endl;
        std::cout << "Select or Enter Your Choice from the Menu:" << std::endl;
        std::cout << "  1. + Summation" << std::endl;
        std::cout << "  2. * Multiply" << std::endl;
        std::cout << "  3. / Division" << std::endl;
        std::cout << "  4. - Subtract" << std::endl;
        std::cout << "  5. Exit" << std::endl;
        std::cout << "=====================================================" << std::endl;
    }
    
    int main() {
        CalcuClass calculator;
        int choice;
        int size;
        std::vector<int> numbers;
    
        do {
            displayMenu();
            std::cout << "Enter your choice: ";
            std::cin >> choice;
    
            if (choice >= 1 && choice <= 4) {
                std::cout << "Enter the number of elements: ";
                std::cin >> size;
                numbers.resize(size);
    
                std::cout << "Enter the elements: ";
                for (int i = 0; i < size; ++i) {
                    std::cin >> numbers[i];
                }
            }
    
            switch (choice) {
                case 1: {
                    int result = calculator.Summation(numbers);
                    std::cout << "Summation result: " << result << std::endl;
                    break;
                }
                case 2: {
                    int result = calculator.Multiply(numbers);
                    std::cout << "Multiplication result: " << result << std::endl;
                    break;
                }
                case 3: {
                    double result = calculator.Division(numbers);
                    std::cout << "Division result: " << result << std::endl;
                    break;
                }
                case 4: {
                    int result = calculator.Subtract(numbers);
                    std::cout << "Subtraction result: " << result << std::endl;
                    break;
                }
                case 5:
                    std::cout << "Exiting the program..." << std::endl;
                    break;
                default:
                    std::cout << "Invalid choice! Please select a valid option." << std::endl;
                    break;
            }
    
        } while (choice != 5);
    
        return 0;
    }
