package AgeCalculator.java; // Add this line

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.time.LocalDate;

public class AgeCalculator extends JFrame {
    private JTextField birthYearField;
    private JLabel resultLabel;

    public AgeCalculator() {
        setTitle("Age Calculator");
        setSize(300, 150);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(null);

        JLabel label = new JLabel("Enter Birth Year:");
        label.setBounds(20, 20, 120, 25);
        add(label);

        birthYearField = new JTextField();
        birthYearField.setBounds(140, 20, 100, 25);
        add(birthYearField);

        JButton button = new JButton("Calculate");
        button.setBounds(80, 50, 120, 30);
        add(button);

        resultLabel = new JLabel("Your age will appear here.");
        resultLabel.setBounds(50, 90, 200, 25);
        add(resultLabel);

        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                calculateAge();
            }
        });

        setVisible(true);
    }

    private void calculateAge() {
        try {
            int year = Integer.parseInt(birthYearField.getText());
            int age = LocalDate.now().getYear() - year;
            resultLabel.setText("You are " + age + " years old.");
        } catch (Exception ex) {
            resultLabel.setText("Invalid year!");
        }
    }

    public static void main(String[] args) {
        new AgeCalculator();
    }
}
