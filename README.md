import java.awt.Color;
import java.awt.EventQueue;
import java.awt.Frame;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPasswordField;
import javax.swing.JTextField;
import javax.swing.UIManager;

public class Login_System {
    private JFrame frame;
    private JTextField txtUsername;
    private JPasswordField txtPassword;
    protected Frame frmLoginSystem;

    public static void main(String[] args) {
        EventQueue.invokeLater(new Runnable() {
            public void run() {
                try {
                    Login_System window = new Login_System();
                    window.frame.setVisible(true);
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        });
    }

    /**
     * Create the application.
     */
    public Login_System() {
        initialize();
    }

    /**
     * Initialize the contents of the frame.
     */
    private void initialize() {
        frame = new JFrame();
        frame.setBounds(200, 200, 500, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.getContentPane().setLayout(null);

        JLabel lblUsername = new JLabel("E-mail");
        lblUsername.setBounds(34, 65, 89, 14);
        frame.getContentPane().add(lblUsername);

        JLabel lblPassword = new JLabel("Password");
        lblPassword.setBounds(34, 136, 73, 14);
        frame.getContentPane().add(lblPassword);

        txtUsername = new JTextField();
        txtUsername.setBounds(117, 62, 213, 20);
        frame.getContentPane().add(txtUsername);
        txtUsername.setColumns(10);

        txtPassword = new JPasswordField();
        txtPassword.setBounds(117, 133, 213, 20);
        frame.getContentPane().add(txtPassword);

        JButton btnLogin = new JButton("Login");
        btnLogin.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String password = txtPassword.getText();
                String name = txtUsername.getText();

                if(password.contains("1234") && name.contains("Vasya")){
                    txtPassword.setText(null);
                    txtUsername.setText(null);
                }
                else{
                    JOptionPane.showConfirmDialog(null, "Не правильный логин или пароль!","Error",JOptionPane.ERROR_MESSAGE);
                    txtPassword.setText(null);
                    txtUsername.setText(null);
                }
            }
        });
        btnLogin.setBounds(34, 214, 89, 37);
        frame.getContentPane().add(btnLogin);

        JButton btnReset = new JButton("Reset");
        btnReset.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                txtUsername.setText(null);
                txtPassword.setText(null);


            }
        });
        btnReset.setBounds(150, 214, 89, 37);
        frame.getContentPane().add(btnReset);

        JButton btnExit = new JButton("Exit");
        btnExit.addActionListener(new ActionListener() {

            public void actionPerformed(ActionEvent e) {

                frmLoginSystem = new Frame("Exit");
                if(JOptionPane.showConfirmDialog(frmLoginSystem, "Вы действительно хотите выйти?","Login Systems",
                        JOptionPane.YES_NO_OPTION)==JOptionPane.YES_NO_OPTION){
                    System.exit(0);
                }

            }
        });
        btnExit.setBounds(385, 214, 89, 37);
        frame.getContentPane().add(btnExit);

        JButton btnCheck_in = new JButton("Check in");
        btnCheck_in.setForeground(Color.BLACK);
        btnCheck_in.setBackground(UIManager.getColor("MenuItem.selectionBackground"));
        btnCheck_in.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                Chech_in info = new Chech_in();
                Chech_in.main(null);

            }
        });
        btnCheck_in.setBounds(262, 214, 89, 37);
        frame.getContentPane().add(btnCheck_in);
    }
}
