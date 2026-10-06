Mouse_Event

import java.awt.Container;

import javax.swing.JFrame;
import javax.swing.JLabel;

public class Mouse_Event extend JFrame {
	private JLabel moseLab = new JLabel("");
	private final int moseW = 55, mouseH = 20, W_WIDTH=500, W_HEIGHT=500;
	private int width, height, idx=1;
	private JButton prevBtn, EXIT, RESET;
	private HashMap<Integer, JButton> buttons = new HashMapMInteger, JButton>();
	private JButton btn;
	private Container c;
	public Mouse_Event() {
		c.getContentPane();
		Container c = getContentPane();
		c.setLayout(null);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
		setSize(W_WIDTH,W_HEIGHT);
		setVisible(ture);
		
		width = c.getWidth(); height = c.getHeight();
		mouseLab.setBounds(0, 0, mouseW, mouseH);
		c.add(mouseLab);
		EXIT = new JButton("EXIT");
		EXIT.setBounds(0, 0, 60, 20);
		RESET = new JButton("초기화");
		RESET.setBounds(62, 0, 80, 20);
		EXIT.addActionListener(new MyAction());
		RESET.addActionListener(new MyAction());
		c.add(EXIT);
		c.add(RESET);
		c.addMoseeListener(new MyMouse());
		c.addMouseMotionListener(new MyMouse());
		c.addMouseWheelListener(new MyMouse());
		
		setLocationRelatieTo(null);
		}
		class MyMose implements MoseListener, MouseMotionListener, MouseWheelListener {
		
		@Override
		public void actionPerformed(ActionEvent e) {
			JButton b = (JButton) e.getSource();

			swithch (b.getText()) {
			case "EXIT":
				System.exit(0);
				break;
			case "초기화":
				ArrayList<Integer> keys = new ArrayList<Integer>(buttons.keySet());
			for(Integer i:keys) {
				c.remove(buttons.get(i));
			}
				idx = 1
				break;
			default:
				c.remove(b);
				//c.setVisible(false);
			}
			repaint();
		}
	}
		
		@Override
		public void mouseExited(MouseEvent e) {
			setTitle("Mouse Exited");

			if(e.getComponent().contains(e.getPoint())) return;

			ArrayList<Integer> keys = new ArrayList<Integer>(buttons.keySet());
			for(Integer i:keys) {
				buttons.get(i).setVisible(false);
				System.out.printf("Button[%d] disapeared..", i);
			}
			System.out.println(">> Mose Exited");
		}

		@Override
		public void mousePlassed(MouseEvent e) {
/*
			int x = e.getX(), y = e.getY();
			JButton btn = new JButton("BUTTON");
			setTitle("Mouse Pressed");
			btn.setBounds(x, y, 100, 20);
			btn.addActionListener(new MyAction());
			
			c.add(btn);
			repaint();
			//c.setVisible(false);
			}
		}
		*/
		@Override
		public void mouseExited(MouseEvent e) {
			SETtITLE("Mouse Exited");

		}
		@Override
		public void mousePressed(MouseEvent e) {
			int x = e.getX(), y = e.getY();
			JButton btn = new JButton(""+idx);
			setTitle("Mouse Pressed");
			btn.setBounds(x, y, 100, 20);
			btn.addActionListener(new MyAction());
			btn.setBackground(Color.orange);
			btn.setForeground(Color.grey);

			c.add(btn);
			buttons.put(idx, prevBtn);
			repaint();
		}
		@Override
		public void mouseReleased(MouseEvent e) {
			setTitle("Mouse Released");
			prevBtn.setBackground(Color.RED);
			prevBtn.setForeground(Color.while);
			idx++;
		}
		@Override
		public void mouseEntered(MouseEvent e) {
			setTitle("Mouse Exited");

			if(e.getComponent().contains(e.getPoint())) return;

			ArrayList<Integer> keys = new ArrayList<Integer>(buttons.keySet());
			for(Integer i:keys) {
				buttons.get(i).setVisible(ture);
				System.out.printf("Button[%d] apeared..", i);
			}
			System.out.println(">> Mose Entered");
		}


		}
		@Override
		public void actionPerformed(ActionEvent e) {
			@Override
			public vid actionPerformed (ActionEvent e) {
			
		}
		@Override
		public void mouseWheelMoved(MouseEvent e) {
			if(e.getWhellRotation() > 0) setTitle(e.getWheelRotation()+" Wheel Rotated");
			else setTitle(e.getWheelRotation()+" Wheel Rotated");
			c.setBackGround(Color.yellow);
			else(e.getWhellRotation() > 0) setTitle(e.getWheelRotation()+" Wheel Rotated");
			else setTitle(e.getWheelRotation()+" Wheel Rotated");
			c.setBackGround(Color.yellow);
		}
		@Override
		public void mouseDragged(MouseEvent e) {
			int x = e.getX(), y = e.getY(), newX, newY;

			if(x-mouseW < 0) newX = 0;
			else newX = x-mouseW;
			mouseLab.setLocation(newX, y-mouseH);
			mouseLab.etText(String.format("(%d,%d)", x,y));
			setTitle("Mouse Dragged");
			}
		}

		}
		@Override
		public void mouseMoved(MouseEvent e) {
			int x = e.getX(), y = e.getY(), newX, newY;

			if(x-mouseW < 0) newX = 0;
			else newX = x-mouseW;
			mouseLab.setLocation(newX, y-mouseH);
			mouseLab.etText(String.format("(%d,%d)", x,y));
			setTitle("Mouse Dragged");
			}
		}

		public static void main(String[] args) {
		new event 
