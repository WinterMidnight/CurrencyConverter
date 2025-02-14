import java.awt.Color;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JComboBox;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JTextField;

public class SimpleCurrencyConverter extends JFrame {

    private JTextField amountField;
    private JComboBox<String> fromCurrencyComboBox;
    private JComboBox<String> toCurrencyComboBox;
    private JLabel resultLabel;

    private final double USD_INR = 74.0;
    private final double USD_AED = 3.67;

    public SimpleCurrencyConverter() {
        setTitle("Simple Currency Converter");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        getContentPane().setBackground(Color.PINK);
        setLayout(new GridLayout(5, 2));

        add(new JLabel("Amount: "));
        amountField = new JTextField();
        add(amountField);

        add(new JLabel("Convert from: "));
        fromCurrencyComboBox = new JComboBox<>(new String[]{"USD", "INR", "AED"});
        add(fromCurrencyComboBox);

        add(new JLabel("Convert to: "));
        toCurrencyComboBox = new JComboBox<>(new String[]{"USD", "INR", "AED"});
        add(toCurrencyComboBox);

        JButton convertButton = new JButton("Convert");
        add(convertButton);

        resultLabel = new JLabel("Converted Amount: ");
        add(resultLabel);

        convertButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                convertCurrency();
            }
        });
    }

    private void convertCurrency() {
        try {
            double amount = Double.parseDouble(amountField.getText());
            if (amount <= 0) {
                throw new NumberFormatException();
            }

            String fromCurrency = (String) fromCurrencyComboBox.getSelectedItem();
            String toCurrency = (String) toCurrencyComboBox.getSelectedItem();

            double convertedAmount = 0;

            if (fromCurrency.equals("USD")) {
                convertedAmount = toCurrency.equals("INR") ? amount * USD_INR : amount * USD_AED;
            } else if (fromCurrency.equals("INR")) {
                convertedAmount = toCurrency.equals("USD") ? amount / USD_INR : amount * (USD_AED / USD_INR);
            } else if (fromCurrency.equals("AED")) {
                convertedAmount = toCurrency.equals("USD") ? amount / USD_AED : amount * (USD_INR / USD_AED);
            }

            resultLabel.setText(String.format("Converted Amount: %.2f %s", convertedAmount, toCurrency));
        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(this, "Please enter an amount.", "Invalid Input", JOptionPane.ERROR_MESSAGE);
        }
    }

    public static void main(String[] args) {
            SimpleCurrencyConverter app = new SimpleCurrencyConverter();
            app.setVisible(true);
        };
    }
