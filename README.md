import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class MakeCar extends JFrame{
    public MakeCar(){
        Car car=new Car();
        add(car);
    }
   
    public static void main(String[] args){
        MakeCar frame=new MakeCar();
        frame.setSize(600,200);
        frame.setLocationRelativeTo(null);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}

class Car extends JPanel{
    private int x=-5;
    private int delay=2;
    private Timer timer=new Timer(20,new TimerListener());
   
    public Car(){
        timer.start();
    }
    public void paintComponent(Graphics g){
        super.paintComponent(g);
        x+=delay;
        int m[]={x+10,x+40,x+30,x+20};
        int n[]={getHeight()-20,getHeight()-20,getHeight()-30,getHeight()-30};
       
        if(x>getWidth()-10) x=-5;
       
        g.setColor(Color.BLACK);
        g.fillOval(x+10, getHeight()-10, 10, 10);
        g.fillOval(x+30, getHeight()-10, 10, 10);
        g.setColor(Color.BLUE);
        g.fillRect(x, getHeight()-20, 50,10);
        g.setColor(Color.RED);
        g.fillPolygon(m,n,m.length);
    }
   
    private class TimerListener implements ActionListener{
        public void actionPerformed(ActionEvent e){
            repaint();
        }
    }
}
