# Rust
Rust Hesap Makinesi

enum Operator {
    Add,
    Subtract,
    Multiply,
    Divide,
}

fn calculate(operator: Operator, num1: f64, num2: f64) -> Option<f64> {
    match operator {
        Operator::Add => Some(num1 + num2),
        Operator::Subtract => Some(num1 - num2),
        Operator::Multiply => Some(num1 * num2),
        Operator::Divide => {
            if num2 == 0.0 {
                None
            } else {
                Some(num1 / num2)
            }
        }
    }
}

fn main() {
    let num1 = 10.0;
    let num2 = 5.0;
    let operator = Operator::Add;

    match calculate(operator, num1, num2) {
        Some(result) => {
            println!("Result: {}", result);
        }
        None => {
            println!("Cannot divide by zero.");
        }
    }
}














Building a Custom Filtering Function in Rust

fn custom_filter<T, F>(iter: impl Iterator<Item = T>, predicate: F) -> Vec<T>
where
    F: Fn(&T) -> bool,
{
    let mut result = Vec::new();

    for item in iter {
        if predicate(&item) {
            result.push(item);
        }
    }

    result
}

fn main() {
    let numbers = vec![1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    // Define a closure for the filtering condition (e.g., keep even numbers).
    let is_even = |x: &i32| *x % 2 == 0;

    // Use the custom filter function.
    let even_numbers = custom_filter(numbers.iter(), is_even);

    // Print the filtered result.
    println!("Even numbers: {:?}", even_numbers);
}
