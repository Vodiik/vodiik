<a href="https://wakatime.com/@43a50c5b-fd67-42a2-8aeb-8bd80f41e38d"><img src="https://wakatime.com/badge/user/43a50c5b-fd67-42a2-8aeb-8bd80f41e38d.svg" alt="Total time coded since May 11 2022" /></a>

<!--
**Vodiik/vodiik** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->


import javax.swing.*;
import java.awt.*;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.awt.image.BufferedImage;

public class Canvas {
    private final JFrame frame;
    private final JPanel panel;
    private final BufferedImage img;

    public Canvas(int width, int height) {

        frame = new JFrame();

        frame.setLayout(new BorderLayout());
        frame.setTitle("UHK FIM PGRF1");
        frame.setResizable(false);
        frame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        img = new BufferedImage(width, height, BufferedImage.TYPE_INT_RGB);

        panel = new JPanel() {
            @Override
            protected void paintComponent(Graphics g) {
                super.paintComponent(g);
                g.drawImage(img, 0, 0, null);
            }
        };

        panel.setPreferredSize(new Dimension(width, height));

        frame.add(panel, BorderLayout.CENTER);
        frame.pack(); //TODO
        frame.setVisible(true);

        panel.requestFocus();
        panel.requestFocusInWindow();

        panel.addKeyListener(new KeyAdapter() {
            @Override
            public void keyPressed(KeyEvent e) {
                super.keyPressed(e);

                int x = height/2;
                int y = width/2;

                if (e.getKeyCode() == KeyEvent.VK_P) {
                    img.setRGB(x, y, 0xff00ff);
                }

                panel.repaint();
            }
        });
    }

}

