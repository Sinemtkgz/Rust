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
