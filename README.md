# project
![img.png](img.png)Varya Semenova
11.12
![img_1.png](img_1.png)
12.01-18.01
from flask import Flask
app = Flask(__name__)
chords = {
    "Am": "E|---0---|\nB|---1---| (Указательный)\nG|---2---| (Безымянный)\nD|---2---| (Средний)\nA|---0---|\nE|---X---|",
    "C": "E|---0---|\nB|---1---| (Указтельный) \nG|---0---|\nD|---2---| (Средний)\nA|---3---| (Безымянный)\nE|---X---|",
    "G": "E|---3---| (Мизинец)\nB|---0---|\nG|---0---|\nD|---0---|\nA|---2---| (Средний)\nE|---3---| (Безымянный)"
}
@app.route('/')
def home():
    html = "<h1>Выбор аккордов:</h1>"
    for name in chords.keys():
        html += f'<p><a href="/chord/{name}">{name}</a></p>'
    return html
@app.route('/chord/<name>')
def show_chord(name):
    info = chords.get(name, "Аккорд не найден")
    return f"""
        <h1>Аккорд {name}</h1>
        <pre style='font-size: 20px;'>{info}</pre>
        <br>
        <a href='/'>Назад к списку</a>
    """
if __name__ == '__main__':
    app.run(debug=True)

from flask import Flask
app = Flask(__name__)

chords = {
    "C": "E|---0---|\nB|---1---| (Указательный)\nG|---0---|\nD|---2---| (Средний)\nA|---3---| (Безымянный)\nE|---X---| (не играется)",
    "C#": "E|---0---|\nB|---1---| (Указательный)\nG|---0---|\nD|---2---| (Средний)\nA|---3---| (Безымянный)\nE|---X---| (не играется) (каподастр 1 лад)",

    "D": "E|---2---| (Средний)\nB|---3---| (Безымянный)\nG|---2---| (Указательный)\nD|---0---|\nA|---X---|\nE|---X---|",
    "D#": "E|---2---| (Средний)\nB|---3---| (Безымянный)\nG|---2---| (Указательный)\nD|---0---|\nA|---X---|\nE|---X---| (каподастр 1 лад)",

    "E": "E|---0---|\nB|---0---|\nG|---1---| (Указательный)\nD|---2---| (Средний)\nA|---2---| (Безымянный)\nE|---0---|",
    "F": "E|---1---| (Указательный, баррэ)\nB|---1---| (Указательный, баррэ)\nG|---2---| (Средний)\nD|---3---| (Безымянный)\nA|---3---| (Мизинец)\nE|---1---| (Указательный, баррэ)",

    "G": "E|---3---| (Мизинец)\nB|---0---|\nG|---0---|\nD|---0---|\nA|---2---| (Средний)\nE|---3---| (Безымянный)",
    "G#": "E|---3---| (Мизинец)\nB|---0---|\nG|---0---|\nD|---0---|\nA|---2---| (Средний)\nE|---3---| (Безымянный) (каподастр 1 лад)",

    "A": "E|---0---|\nB|---2---| (Средний)\nG|---2---| (Безымянный)\nD|---2---| (Указательный)\nA|---0---|\nE|---X---|",
    "A#": "E|---0---|\nB|---2---| (Средний)\nG|---2---| (Безымянный)\nD|---2---| (Указательный)\nA|---0---|\nE|---X---| (каподастр 1 лад)",

    "B": "E|---2---| (Средний)\nB|---0---|\nG|---2---| (Безымянный)\nD|---1---| (Указательный)\nA|---0---|\nE|---X---|",

    "Cm": "E|---3---| (Мизинец)\nB|---4---| (Безымянный)\nG|---3---| (Средний)\nD|---3---| (Указательный)\nA|---X---|\nE|---X---|",
    "C#m": "E|---3---| (Мизинец)\nB|---4---| (Безымянный)\nG|---3---| (Средний)\nD|---3---| (Указательный)\nA|---X---|\nE|---X---| (каподастр 1 лад)",

    "Dm": "E|---1---| (Указательный)\nB|---3---| (Безымянный)\nG|---2---| (Средний)\nD|---0---|\nA|---X---|\nE|---X---|",
    "D#m": "E|---1---| (Указательный)\nB|---3---| (Безымянный)\nG|---2---| (Средний)\nD|---0---|\nA|---X---|\nE|---X---| (каподастр 1 лад)",

    "Em": "E|---0---|\nB|---0---|\nG|---0---|\nD|---2---| (Средний)\nA|---2---| (Безымянный)\nE|---0---|",
    "Fm": "E|---1---| (Указательный, баррэ)\nB|---1---| (Указательный, баррэ)\nG|---1---| (Указательный, баррэ)\nD|---3---| (Безымянный)\nA|---3---| (Мизинец)\nE|---1---| (Указательный, баррэ)",

    "Gm": "E|---3---| (Мизинец)\nB|---3---| (Безымянный)\nG|---3---| (Указательный, баррэ)\nD|---5---| (Средний)\nA|---5---| (Безымянный?)\nE|---3---| (Указательный, баррэ)",
    "G#m": "E|---4---| (Мизинец)\nB|---4---| (Безымянный)\nG|---4---| (Указательный, баррэ)\nD|---6---| (Средний)\nA|---6---| (Безымянный?)\nE|---4---| (Указательный, баррэ)",

    "Am": "E|---0---|\nB|---1---| (Указательный)\nG|---2---| (Средний)\nD|---2---| (Безымянный)\nA|---0---|\nE|---X---|",
    "A#m": "E|---0---|\nB|---1---| (Указательный)\nG|---2---| (Средний)\nD|---2---| (Безымянный)\nA|---0---|\nE|---X---| (каподастр 1 лад)",

    "Bm": "E|---2---| (Средний)\nB|---3---| (Безымянный)\nG|---4---| (Мизинец)\nD|---2---| (Указательный)\nA|---X---|\nE|---X---|",

    "C7": "E|---0---|\nB|---1---| (Указательный)\nG|---0---|\nD|---2---| (Средний)\nA|---3---| (Безымянный)\nE|---X---|",
    "D7": "E|---2---| (Средний)\nB|---1---| (Указательный)\nG|---2---| (Безымянный)\nD|---0---|\nA|---X---|\nE|---X---|",
    "E7": "E|---0---|\nB|---0---|\nG|---1---| (Указательный)\nD|---0---|\nA|---2---| (Средний)\nE|---0---|",
    "G7": "E|---1---| (Указательный)\nB|---0---|\nG|---0---|\nD|---0---|\nA|---2---| (Средний)\nE|---3---| (Безымянный)",
    "A7": "E|---0---|\nB|---2---| (Средний)\nG|---0---|\nD|---2---| (Безымянный)\nA|---0---|\nE|---X---|",
    "B7": "E|---2---| (Средний)\nB|---0---|\nG|---2---| (Безымянный)\nD|---1---| (Указательный)\nA|---0---|\nE|---2---| (Средний?)",


    "Cmaj7": "E|---0---|\nB|---0---|\nG|---0---|\nD|---2---| (Средний)\nA|---3---| (Безымянный)\nE|---X---|",
    "Dmaj7": "E|---2---| (Средний)\nB|---2---| (Средний)\nG|---2---| (Указательный?)\nD|---0---|\nA|---X---|\nE|---X---|",
    "Emaj7": "E|---0---|\nB|---0---|\nG|---1---| (Указательный)\nD|---1---| (Указательный?)\nA|---2---| (Средний)\nE|---0---|",
    "Amaj7": "E|---0---|\nB|---2---| (Средний)\nG|---1---| (Указательный)\nD|---2---| (Безымянный)\nA|---0---|\nE|---X---|",

    "Am7": "E|---0---|\nB|---1---| (Указательный)\nG|---0---|\nD|---2---| (Средний)\nA|---0---|\nE|---X---|",
    "Dm7": "E|---1---| (Указательный)\nB|---1---| (Указательный)\nG|---2---| (Средний)\nD|---0---|\nA|---X---|\nE|---X---|",
    "Em7": "E|---0---|\nB|---0---|\nG|---0---|\nD|---0---|\nA|---2---| (Средний)\nE|---0---|",
    "Gm7": "E|---1---| (Указательный)\nB|---1---| (Указательный)\nG|---0---|\nD|---0---|\nA|---2---| (Средний)\nE|---3---| (Безымянный)",
}


@app.route('/')
def home():
    html = """
    <h1>Выбор аккордов:</h1>
    <style>
        .chord-button {
            display: inline-block;
            margin: 5px;
            padding: 10px 20px;
            background-color: #3CB371;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-size: 17px;
            transition: background-color 0.3s;
        }
        .chord-button:hover {
            background-color: #32CD32;
        }
        .button-container {
            max-width: 800px;
            margin: 0 auto;
        }
    </style>
    <div class="button-container">
    """

    for name in chords.keys():
        html += f'<a href="/chord/{name}" class="chord-button">{name}</a>'

    html += "</div>"
    return html




@app.route('/chord/<name>')
def show_chord(name):
    info = chords.get(name, "Аккорд не найден")
    return f"""
        <h1>Аккорд {name}</h1>
        <pre style='font-size: 20px; background-color: #f0f0f0; padding: 20px; border-radius: 10px;'>{info}</pre>
        <br>
        <a href='/' style="
            display: inline-block;
            padding: 10px 20px;
            background-color: #008CBA;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-size: 16px;
        ">← Назад к списку</a>
    """



if __name__ == '__main__':
    app.run(debug=True)
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.Random;
import java.util.ArrayList;
import java.util.Collections;
import javax.sound.sampled.*;

public class Main extends JPanel implements ActionListener {
int gameState = 0;
int birdY = 250;
int birdX = 100;
int targetY = 250;
double lerpSpeed = 0.12;
int score = 0;
int hoveredButton = -1;
int scrollOffset = 0;
int stabilityCounter = 0;
int potentialTargetY = 250;
ArrayList<Integer> highScores = new ArrayList<>();

    boolean isMuted = false;
    double velocity = 0;
    double gravityConstant = 0.8;
    double jumpPower = -11.0;

    ArrayList<String> selectedChords = new ArrayList<>();

    int pipeWidth = 70;
    int pipeLipHeight = 20;
    int pipeLipExtension = 8;

    int freqHigh = 450;
    int freqMidHigh = 350;
    int freqMid = 250;
    int freqMidLow = 200;
    int freqLow = 150;

    double currentFreq = 0;
    int currentAmp = 0;
    int lastAmp = 0;
    int detectedPeakFreq = 0;

    ArrayList<Integer> freqHistory = new ArrayList<>();
    JTextField[] freqInputs = new JTextField[5];
    JButton[] saveButtons = new JButton[5];


    int minStability = 3;
    int minAmplitude = 800;


    int pixelSize = 4;
    int[][] pixelBird = {
            {0,0,0,0,1,1,1,1,1,0,0}, {0,0,1,1,2,2,2,2,2,1,0}, {0,1,2,2,2,2,2,2,2,2,1},
            {1,2,2,2,2,2,3,6,2,2,1}, {1,2,2,2,2,2,3,3,2,2,1}, {1,2,2,2,2,2,2,2,2,4,1},
            {1,2,2,5,5,2,2,2,4,4,1}, {0,1,2,2,5,5,2,2,2,1,0}, {0,0,1,1,2,2,2,2,1,0,0},
            {0,0,0,0,1,1,1,1,0,0,0}
    };

    Color colBirdBody = new Color(255, 240, 100);
    Color colBirdOutline = new Color(70, 50, 20);
    Color colBirdLips = new Color(255, 120, 70);
    Color colBirdCheek = new Color(255, 180, 200);
    Color colBirdEye = Color.WHITE;

    int numClouds = 10;
    double[] cloudsX = new double[10];
    int[] cloudsY = new int[10];
    double[] cloudsSpeed = new double[10];

    int[] pipesX = {800, 1300, 1800};
    int[] pipesGapY = new int[3];
    String[] pipeChords = new String[3];
    String[] currentLevelChords;

    String[][] levels = {
            {"Am", "Em", "C", "D", "E", "A"},
            {"F", "G", "Am", "Em", "Dm", "C", "A"},
            {"Bm", "Gm", "Cm", "Fm", "Am", "Em", "A"},
            {"F", "G_bar", "A_bar", "B_bar", "C_bar"},
            {"F", "Bm", "Gm", "C_bar", "D_bar", "B7"}
    };

    String[] allChords = {
            "Am", "Em", "C", "G", "D", "E", "A", "F", "Dm",
            "A7", "B7", "C7", "D7", "E7", "G7",
            "Am7", "Dm7", "Em7", "Cmaj7", "Gmaj7", "Dmaj7",
            "Asus4", "Dsus4", "Esus4", "Bm", "Gm", "Cm", "Fm",
            "F#m", "G#m", "C#m", "F#", "G#", "G_bar", "A_bar"
    };

    Random rnd = new Random();
    boolean isGameOver = false;
    boolean showHints = true;
    Timer timer = new Timer(20, this);


    Color colBg = new Color(135, 206, 250);
    Color colPipe = new Color(152, 251, 152);
    Color colPipeDark = new Color(60, 179, 113);
    Color colCloud = Color.WHITE;
    Color colMenuBg = new Color(70, 70, 110);
    Color colBtn = new Color(255, 180, 50);
    Color colBtnHover = new Color(255, 220, 100);
    Color colText = Color.WHITE;
    Color colGreenHover = new Color(130, 255, 130);
    Color colRedHover = new Color(255, 130, 130);
    Color colBlueHover = new Color(180, 230, 255);

    Font fontTitle = new Font(Font.MONOSPACED, Font.BOLD, 45);
    Font fontBtn = new Font(Font.MONOSPACED, Font.BOLD, 18);
    Font fontDesc = new Font(Font.MONOSPACED, Font.PLAIN, 12);
    Font fontChord = new Font(Font.MONOSPACED, Font.BOLD, 30);
    Font fontScore = new Font(Font.MONOSPACED, Font.BOLD, 40);

    public Main() {
        setLayout(null);
        timer.start();
        setFocusable(true);
        requestFocusInWindow();
        initCalibrationUI();
        initClouds();
        startMic();

        for (int i = 0; i < 10; i++) {
            highScores.add(0);
        }

        addMouseListener(new MouseAdapter() {
            public void mousePressed(MouseEvent e) {
                int mx = e.getX();
                int my = e.getY();
                if (gameState == 0) {
                    checkMenuClick(mx, my);
                } else if (gameState == 1) {
                    if (isGameOver) {
                        gameState = 0;
                    } else {
                        if (mx > 680 && mx < 780 && my > 10 && my < 50) {
                            showHints = !showHints;
                        }
                        if (mx > 570 && mx < 670 && my > 10 && my < 50) {
                            isMuted = !isMuted;
                        }
                    }
                } else if (gameState == 2 || gameState == 3) {
                    if (mx < 150 && my < 80) {
                        gameState = 0;
                        toggleFields(false);
                        repaint();
                    }
                } else if (gameState == 4) {
                    handleCreatorClick(mx, my);
                }
            }
        });

        addMouseMotionListener(new MouseAdapter() {
            public void mouseMoved(MouseEvent e) {
                checkMenuHover(e.getX(), e.getY());
            }
        });

        addMouseWheelListener(e -> {
            if (gameState == 3 || gameState == 4) {
                scrollOffset = scrollOffset - e.getWheelRotation() * 35;
                if (scrollOffset > 0) {
                    scrollOffset = 0;
                }
                if (scrollOffset < -600) {
                    scrollOffset = -600;
                }
                repaint();
            }
        });

        addKeyListener(new KeyAdapter() {
            public void keyPressed(KeyEvent e) {
                if (gameState == 1) {
                    if (isGameOver == true) {
                        if (e.getKeyCode() == KeyEvent.VK_SPACE) {
                            restartGame();
                        }
                    }
                    if (isGameOver == false) {
                        if (isMuted == true) {
                            if (e.getKeyCode() == KeyEvent.VK_SPACE) {
                                velocity = jumpPower;
                            }
                        }
                    }
                }
            }
        });
    }

    void checkMenuHover(int mx, int my) {
        int oldHover = hoveredButton;
        hoveredButton = -1;

        if (gameState == 0) {
            if (mx > 210 && mx < 590) {
                for (int i = 0; i < 5; i++) {
                    if (my > 110 + i * 80 && my < 165 + i * 80) {
                        hoveredButton = i;
                        break;
                    }
                }
            }
            if (mx > 610 && mx < 780) {
                if (my > 360 && my < 410) {
                    hoveredButton = 5;
                } else if (my > 420 && my < 470) {
                    hoveredButton = 6;
                } else if (my > 480 && my < 530) {
                    hoveredButton = 7;
                }
            }
        } else if (gameState == 1) {
            if (isGameOver == false) {
                if (my > 10 && my < 50) {
                    if (mx > 570 && mx < 670) {
                        hoveredButton = 8;
                    } else if (mx > 680 && mx < 780) {
                        hoveredButton = 9;
                    }
                }
            }
        }

        if (oldHover != hoveredButton) {
            repaint();
        }
    }

    void initClouds() {
        for (int i = 0; i < numClouds; i++) {
            cloudsX[i] = rnd.nextInt(900);
            cloudsY[i] = rnd.nextInt(350) + 30;
            cloudsSpeed[i] = 0.5 + rnd.nextDouble() * 1.5;
        }
    }

    void handleCreatorClick(int mx, int my) {
        if (mx < 120 && my < 50) {
            gameState = 0;
            return;
        }
        if (mx > 650 && my < 50) {
            if (selectedChords.isEmpty() == false) {
                currentLevelChords = selectedChords.toArray(new String[0]);
                restartGame();
                gameState = 1;
                return;
            }
        }
        for (int i = 0; i < allChords.length; i++) {
            int col = i % 8;
            int row = i / 8;
            int x = 20 + col * 95;
            int y = 80 + row * 125 + scrollOffset;
            if (mx > x && mx < x + 90 && my > y && my < y + 120) {
                if (selectedChords.contains(allChords[i])) {
                    selectedChords.remove(allChords[i]);
                } else {
                    selectedChords.add(allChords[i]);
                }
                repaint();
                break;
            }
        }
    }

    void initCalibrationUI() {
        for (int i = 0; i < 5; i++) {
            freqInputs[i] = new JTextField();
            freqInputs[i].setBounds(55 + i * 150, 370, 110, 30);
            freqInputs[i].setVisible(false);
            add(freqInputs[i]);

            int idx = i;
            saveButtons[i] = new JButton("SAVE");
            saveButtons[i].setBounds(55 + i * 150, 410, 110, 30);
            saveButtons[i].setBackground(new Color(100, 255, 100));
            saveButtons[i].setVisible(false);
            saveButtons[i].addActionListener(e -> {
                try {
                    int val = Integer.parseInt(freqInputs[idx].getText());
                    if (idx == 0) { freqHigh = val; }
                    else if (idx == 1) { freqMidHigh = val; }
                    else if (idx == 2) { freqMid = val; }
                    else if (idx == 3) { freqMidLow = val; }
                    else if (idx == 4) { freqLow = val; }
                    requestFocusInWindow();
                } catch (Exception ex) {}
            });
            add(saveButtons[i]);
        }
    }

    void toggleFields(boolean v) {
        for (int i = 0; i < 5; i++) {
            freqInputs[i].setVisible(v);
            saveButtons[i].setVisible(v);
        }
    }

    void checkMenuClick(int mx, int my) {
        if (mx > 210 && mx < 590) {
            for (int i = 0; i < 5; i++) {
                if (my > 110 + i * 80 && my < 170 + i * 80) {
                    currentLevelChords = levels[i];
                    restartGame();
                    gameState = 1;
                    return;
                }
            }
        }
        if (mx > 610 && mx < 780) {
            if (my > 360 && my < 410) {
                gameState = 4;
                scrollOffset = 0;
                selectedChords.clear();
            } else if (my > 420 && my < 470) {
                gameState = 3;
                scrollOffset = 0;
            } else if (my > 480 && my < 530) {
                gameState = 2;
                toggleFields(true);
            }
            repaint();
        }
    }

    void restartGame() {
        birdY = 250;
        targetY = 250;
        velocity = 0;
        isGameOver = false;
        score = 0;
        for (int i = 0; i < 3; i++) {
            pipesX[i] = 800 + i * 500;
            generatePipe(i);
        }
        initClouds();
    }

    void generatePipe(int i) {
        int rIndex = rnd.nextInt(currentLevelChords.length);
        pipeChords[i] = currentLevelChords[rIndex];
        pipesGapY[i] = getGapY(pipeChords[i]);
    }

    int getGapY(String c) {
        if (c.equals("D") || c.contains("D_bar") || c.equals("A_bar") || c.equals("F#") || c.equals("A")) {
            return 70;
        }
        if (c.equals("C") || c.contains("C_bar") || c.contains("B")) {
            return 160;
        }
        if (c.contains("Am") || c.equals("Cm") || c.equals("B7")) {
            return 250;
        }
        if (c.equals("Em") || c.equals("Gm") || c.equals("Fm") || c.equals("E")) {
            return 340;
        }
        return 430;
    }

    void updateHighScores() {
        highScores.add(score);
        Collections.sort(highScores, Collections.reverseOrder());
        while (highScores.size() > 10) {
            highScores.remove(10);
        }
    }

    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        if (gameState == 0) {
            drawMenu(g);
        } else if (gameState == 1) {
            drawGame(g);
        } else if (gameState == 2) {
            drawCalibration(g);
        } else if (gameState == 3) {
            drawLibrary(g);
        } else if (gameState == 4) {
            drawCreator(g);
        }
    }

    void drawMenu(Graphics g) {
        g.setColor(colMenuBg);
        g.fillRect(0, 0, 800, 600);
        drawPixelCloud(g, 100, 50);
        drawPixelCloud(g, 600, 80);

        g.setColor(Color.BLACK);
        g.setFont(fontTitle);
        g.drawString("flappybird", 234, 74);
        g.setColor(colText);
        g.drawString("flappybird", 230, 70);

        g.setColor(new Color(40, 40, 80));
        g.fillRoundRect(20, 110, 160, 410, 15, 15);
        g.setColor(Color.WHITE);
        g.setFont(fontBtn);
        g.drawString("TOP SCORES", 45, 140);
        g.drawLine(30, 145, 170, 145);

        g.setFont(new Font(Font.MONOSPACED, Font.BOLD, 16));
        for (int i = 0; i < 10; i++) {
            g.setColor(new Color(200, 200, 255));
            g.drawString((i + 1) + ". ", 40, 180 + i * 34);
            g.setColor(Color.WHITE);
            g.drawString(highScores.get(i).toString(), 85, 180 + i * 34);
        }

        for (int i = 0; i < 5; i++) {
            if (i == hoveredButton) {
                g.setColor(colBtnHover);
            } else {
                g.setColor(colBtn);
            }
            g.fillRect(210, 110 + i * 80, 380, 55);
            g.setColor(Color.BLACK);
            g.drawRect(210, 110 + i * 80, 380, 55);
            g.setFont(fontBtn);
            g.drawString("LEVEL " + (i + 1), 230, 135 + i * 80);
            g.setFont(fontDesc);
            g.drawString("Chords: " + String.join(", ", levels[i]), 230, 155 + i * 80);
        }

        // Кнопки справа
        if (hoveredButton == 5) {
            g.setColor(colBlueHover);
        } else {
            g.setColor(new Color(100, 200, 255));
        }
        g.fillRect(610, 360, 165, 50);
        g.setColor(Color.BLACK);
        g.drawRect(610, 360, 165, 50);
        g.setFont(fontBtn);
        g.drawString("MY LEVEL", 645, 392);

        if (hoveredButton == 6) {
            g.setColor(colBtnHover);
        } else {
            g.setColor(colBtn);
        }
        g.fillRect(610, 420, 165, 50);
        g.setColor(Color.BLACK);
        g.drawRect(610, 420, 165, 50);
        g.drawString("CHORDS LIB", 635, 452);

        if (hoveredButton == 7) {
            g.setColor(colBtnHover);
        } else {
            g.setColor(colBtn);
        }
        g.fillRect(610, 480, 165, 50);
        g.setColor(Color.BLACK);
        g.drawRect(610, 480, 165, 50);
        g.drawString("CALIBRATE", 635, 512);
    }
    void drawCreator(Graphics g) {
        g.setColor(colMenuBg);
        g.fillRect(0, 0, 800, 600);
        for (int i = 0; i < allChords.length; i++) {
            int col = i % 8;
            int row = i / 8;
            int x = 20 + col * 95;
            int y = 80 + row * 125 + scrollOffset;
            if (selectedChords.contains(allChords[i])) {
                g.setColor(new Color(255, 255, 100));
                g.fillRect(x - 3, y - 3, 91, 126);
            }
            drawChordGrid(g, allChords[i], x, y, 0.8);
        }
        g.setColor(colMenuBg);
        g.fillRect(0, 0, 800, 65);
        g.setColor(colBtn);
        g.fillRect(20, 15, 100, 35);
        g.setFont(fontBtn);
        g.setColor(Color.BLACK);
        g.drawString("BACK", 42, 38);

        if (selectedChords.isEmpty()) {
            g.setColor(Color.GRAY);
        } else {
            g.setColor(new Color(100, 255, 100));
        }
        g.fillRect(650, 15, 120, 35);
        g.setColor(Color.BLACK);
        g.drawRect(650, 15, 120, 35);
        g.drawString("START", 685, 38);
        g.setColor(Color.WHITE);
        g.setFont(new Font(Font.MONOSPACED, Font.BOLD, 25));
        g.drawString("SELECT CHORDS: " + selectedChords.size(), 240, 40);
    }

    void drawLibrary(Graphics g) {
        g.setColor(colMenuBg);
        g.fillRect(0, 0, 800, 600);
        for (int i = 0; i < allChords.length; i++) {
            int col = i % 8;
            int row = i / 8;
            drawChordGrid(g, allChords[i], 20 + col * 95, 80 + row * 125 + scrollOffset, 0.8);
        }
        g.setColor(colMenuBg);
        g.fillRect(0, 0, 800, 65);
        g.setColor(colBtn);
        g.fillRect(20, 15, 100, 35);
        g.setColor(Color.BLACK);
        g.drawRect(20, 15, 100, 35);
        g.setFont(fontBtn);
        g.drawString("BACK", 42, 38);
        g.setColor(Color.WHITE);
        g.setFont(new Font(Font.MONOSPACED, Font.BOLD, 30));
        g.drawString("CHORD LIBRARY", 280, 40);
    }

    void drawCalibration(Graphics g) {
        g.setColor(colMenuBg);
        g.fillRect(0, 0, 800, 600);
        g.setColor(colBtn);
        g.fillRect(20, 20, 100, 40);
        g.setColor(Color.BLACK);
        g.drawRect(20, 20, 100, 40);
        g.setFont(fontBtn);
        g.drawString("BACK", 40, 47);

        int gx = 400; int gy = 40; int gw = 360; int gh = 180;
        g.setColor(new Color(20, 20, 30));
        g.fillRect(gx, gy, gw, gh);
        g.setColor(new Color(60, 60, 80));
        for (int i = 1; i <= 4; i++) {
            g.drawLine(gx, gy + gh - (i * gh / 5), gx + gw, gy + gh - (i * gh / 5));
        }
        g.setColor(Color.CYAN);
        if (freqHistory.size() > 1) {
            for (int i = 0; i < freqHistory.size() - 1; i++) {
                int x1 = gx + gw - (i * 6);
                int x2 = gx + gw - ((i + 1) * 6);
                int y1 = (gy + gh) - (int)(Math.min(1000, freqHistory.get(i)) * gh / 1000.0);
                int y2 = (gy + gh) - (int)(Math.min(1000, freqHistory.get(i+1)) * gh / 1000.0);
                if (x2 >= gx) {
                    g.drawLine(x1, y1, x2, y2);
                }
            }
        }
        g.setColor(Color.WHITE);
        g.fillRect(150, 40, 200, 180);
        g.setColor(Color.BLACK);
        g.drawRect(150, 40, 200, 180);
        g.setFont(fontDesc);
        g.drawString("CURRENT Hz:", 160, 65);
        g.setFont(fontChord);
        g.drawString((int)currentFreq + "", 160, 100);
        g.setColor(new Color(200, 0, 0));
        g.setFont(fontDesc);
        g.drawString("LAST PEAK DETECTED:", 160, 140);
        g.setFont(fontChord);
        g.drawString(detectedPeakFreq + " Hz", 160, 180);

        String[] labels = {"D (Top)", "C", "Am", "Em", "G (Bot)"};
        int[] saved = {freqHigh, freqMidHigh, freqMid, freqMidLow, freqLow};
        for (int i = 0; i < 5; i++) {
            g.setColor(Color.WHITE);
            g.fillRect(50 + i * 150, 250, 120, 200);
            g.setColor(Color.BLACK);
            g.setFont(fontBtn);
            g.drawString(labels[i], 55 + i * 150, 280);
            g.setFont(fontChord);
            g.drawString("" + saved[i], 60 + i * 150, 330);
            g.setFont(fontDesc);
            g.drawString("SAVED", 85 + i * 150, 350);
        }
    }

    void drawGame(Graphics g) {
        g.setColor(colBg);
        g.fillRect(0, 0, 800, 600);
        for (int i = 0; i < numClouds; i++) {
            drawPixelCloud(g, (int)cloudsX[i], cloudsY[i]);
        }
        g.setColor(Color.BLACK);
        g.setFont(fontScore);
        g.drawString("" + score, 403, 53);
        g.setColor(Color.WHITE);
        g.drawString("" + score, 400, 50);

        
        if (isMuted) {
            if (hoveredButton == 8) { g.setColor(colRedHover); } else { g.setColor(Color.RED); }
        } else {
            if (hoveredButton == 8) { g.setColor(colGreenHover); } else { g.setColor(Color.GREEN); }
        }
        g.fillRect(570, 10, 100, 40);
        g.setColor(Color.BLACK);
        g.drawRect(570, 10, 100, 40);
        g.setFont(fontBtn);
        if (isMuted) { g.drawString("SPACE", 595, 37); } else { g.drawString("MIC", 595, 37); }

        
        if (hoveredButton == 9) { g.setColor(colBlueHover); }
        else { if (showHints) { g.setColor(colBtn); } else { g.setColor(Color.GRAY); } }
        g.fillRect(680, 10, 100, 40);
        g.setColor(Color.BLACK);
        g.drawRect(680, 10, 100, 40);
        g.setFont(fontBtn);
        g.drawString("HINTS", 700, 37);

        
        for (int r = 0; r < pixelBird.length; r++) {
            for (int c = 0; c < pixelBird[0].length; c++) {
                int code = pixelBird[r][c];
                if (code != 0) {
                    if (code == 1) { g.setColor(colBirdOutline); }
                    else if (code == 2) { g.setColor(colBirdBody); }
                    else if (code == 3) { g.setColor(colBirdEye); }
                    else if (code == 4) { g.setColor(colBirdLips); }
                    else if (code == 5) { g.setColor(colBirdCheek); }
                    else if (code == 6) { g.setColor(Color.BLACK); }
                    g.fillRect(birdX + c * pixelSize, birdY + r * pixelSize, pixelSize, pixelSize);
                }
            }
        }

        for (int i = 0; i < 3; i++) {
            int tx = pipesX[i];
            int gapCenter = pipesGapY[i];
            int gapHalf = 130;
            int gapTop = gapCenter - gapHalf;
            int gapBottom = gapCenter + gapHalf;
            g.setColor(colPipe);
            g.fillRect(tx, 0, pipeWidth, gapTop); 
            g.setColor(colPipeDark);
            g.drawRect(tx, -1, pipeWidth, gapTop + 1); 
            g.setColor(colPipe);
            g.fillRect(tx - pipeLipExtension, gapTop - pipeLipHeight, pipeWidth + pipeLipExtension * 2, pipeLipHeight);
            g.setColor(colPipeDark);
            g.drawRect(tx - pipeLipExtension, gapTop - pipeLipHeight, pipeWidth + pipeLipExtension * 2, pipeLipHeight);
            g.setColor(colPipe);
            g.fillRect(tx - pipeLipExtension, gapBottom, pipeWidth + pipeLipExtension * 2, pipeLipHeight);
            g.setColor(colPipeDark);
            g.drawRect(tx - pipeLipExtension, gapBottom, pipeWidth + pipeLipExtension * 2, pipeLipHeight);
            g.setColor(colPipe);
            g.fillRect(tx, gapBottom + pipeLipHeight, pipeWidth, 600);
            g.setColor(colPipeDark);
            g.drawRect(tx, gapBottom + pipeLipHeight, pipeWidth, 600);
            g.setColor(Color.WHITE);
            g.setFont(fontChord);
            g.drawString(pipeChords[i].replace("_bar",""), tx + 5, gapCenter + 10);
            if (showHints) {
                if (tx > birdX - 50 && tx < birdX + 450) {
                    drawChordGrid(g, pipeChords[i], 660, 60, 1.0);
                }
            }
        }

        if (isGameOver) {
            g.setColor(new Color(0, 0, 0, 200));
            g.fillRect(0, 0, 800, 600);
            g.setColor(Color.WHITE);
            g.setFont(fontTitle);
            g.drawString("GAME OVER", 270, 250);
            g.setFont(fontBtn);
            g.drawString("Score: " + score, 340, 300);
            g.drawString("Press SPACE to Retry", 280, 380);
            g.setFont(fontDesc);
            g.drawString("Click anywhere to Menu", 325, 410);
        }
    }

    void drawChordGrid(Graphics g, String chord, int x, int y, double scale) {
        int[] dots = {-1, -1, -1, -1, -1, -1};
        int startFret = 0;

        if (chord.equals("Am")) { dots = new int[]{0, 1, 2, 2, 0, -1}; }
        else if (chord.equals("Em")) { dots = new int[]{0, 0, 0, 2, 2, 0}; }
        else if (chord.equals("C")) { dots = new int[]{0, 1, 0, 2, 3, -1}; }
        else if (chord.equals("G")) { dots = new int[]{3, 0, 0, 0, 2, 3}; }
        else if (chord.equals("D")) { dots = new int[]{2, 3, 2, 0, -1, -1}; }
        else if (chord.equals("E")) { dots = new int[]{0, 0, 1, 2, 2, 0}; }
        else if (chord.equals("A")) { dots = new int[]{0, 2, 2, 2, 0, -1}; }
        else if (chord.equals("F")) { dots = new int[]{1, 1, 2, 3, 3, 1}; startFret = 1; }
        else if (chord.equals("Dm")) { dots = new int[]{1, 3, 2, 0, -1, -1}; }
        else if (chord.equals("Bm")) { dots = new int[]{2, 3, 4, 4, 2, -1}; startFret = 2; }
        else if (chord.equals("Gm")) { dots = new int[]{3, 3, 3, 5, 5, 3}; startFret = 3; }
        else if (chord.equals("Cm")) { dots = new int[]{3, 4, 5, 5, 3, -1}; startFret = 3; }
        else if (chord.equals("Fm")) { dots = new int[]{1, 1, 1, 3, 3, 1}; startFret = 1; }
        else if (chord.equals("A7")) { dots = new int[]{0, 2, 0, 2, 0, -1}; }
        else if (chord.equals("B7")) { dots = new int[]{2, 0, 2, 1, 2, -1}; }
        else if (chord.equals("C7")) { dots = new int[]{0, 1, 3, 2, 3, -1}; }
        else if (chord.equals("D7")) { dots = new int[]{2, 1, 2, 0, -1, -1}; }
        else if (chord.equals("E7")) { dots = new int[]{0, 0, 1, 0, 2, 0}; }
        else if (chord.equals("G7")) { dots = new int[]{1, 0, 0, 0, 2, 3}; }
        else if (chord.equals("Am7")) { dots = new int[]{0, 1, 0, 2, 0, -1}; }
        else if (chord.equals("Dm7")) { dots = new int[]{1, 1, 2, 0, -1, -1}; }
        else if (chord.equals("Em7")) { dots = new int[]{0, 0, 0, 0, 2, 0}; }
        else if (chord.equals("Cmaj7")) { dots = new int[]{0, 0, 0, 2, 3, -1}; }
        else if (chord.equals("Gmaj7")) { dots = new int[]{2, 0, 0, 0, 2, 3}; }
        else if (chord.equals("Dmaj7")) { dots = new int[]{2, 2, 2, 0, -1, -1}; }
        else if (chord.equals("Asus4")) { dots = new int[]{0, 3, 2, 2, 0, -1}; }
        else if (chord.equals("Dsus4")) { dots = new int[]{3, 3, 2, 0, -1, -1}; }
        else if (chord.equals("Esus4")) { dots = new int[]{0, 0, 2, 2, 2, 0}; }
        else if (chord.equals("F#m")) { dots = new int[]{2, 2, 2, 4, 4, 2}; startFret = 2; }
        else if (chord.equals("G#m")) { dots = new int[]{4, 4, 4, 6, 6, 4}; startFret = 4; }
        else if (chord.equals("C#m")) { dots = new int[]{4, 5, 6, 6, 4, -1}; startFret = 4; }
        else if (chord.equals("F#")) { dots = new int[]{2, 2, 3, 4, 4, 2}; startFret = 2; }
        else if (chord.equals("G#")) { dots = new int[]{4, 4, 5, 6, 6, 4}; startFret = 4; }
        else if (chord.contains("_bar")) {
            int f = 3;
            if (chord.equals("G_bar")) { f = 3; }
            else if (chord.equals("A_bar")) { f = 5; }
            else if (chord.equals("B_bar")) { f = 7; }
            else if (chord.equals("C_bar")) { f = 8; }
            else { f = 10; }
            dots = new int[]{f, f, f + 1, f + 2, f + 2, f};
            startFret = f;
        }

        int bw = (int)(110 * scale);
        int bh = (int)(150 * scale);
        g.setColor(Color.WHITE);
        g.fillRect(x, y, bw, bh);
        g.setColor(Color.BLACK);
        g.drawRect(x, y, bw, bh);
        int gridX = x + (int)(18 * scale);
        int gridY = y + (int)(32 * scale);
        int stepW = (int)(12 * scale);
        int stepH = (int)(18 * scale);
        g.setColor(Color.BLACK);
        g.setFont(new Font(Font.MONOSPACED, Font.BOLD, (int)(15 * scale)));
        g.drawString(chord.replace("_bar",""), gridX, y + (int)(16 * scale));
        if (startFret > 0) {
            g.setColor(new Color(180, 0, 0));
            g.setFont(new Font(Font.SANS_SERIF, Font.BOLD, (int)(13 * scale)));
            g.drawString(String.valueOf(startFret), x + (int)(3 * scale), gridY + (int)(13 * scale));
        }
        g.setColor(Color.LIGHT_GRAY);
        for (int i = 0; i < 6; i++) {
            g.drawLine(gridX + i * stepW, gridY, gridX + i * stepW, gridY + 5 * stepH);
            g.drawLine(gridX, gridY + i * stepH, gridX + 5 * stepW, gridY + i * stepH);
        }
        for (int s = 0; s < 6; s++) {
            int f = dots[s];
            if (f == 0) {
                g.setColor(Color.BLUE);
                g.drawOval(gridX + (5 - s) * stepW - 4, gridY - 8, 8, 8);
            } else if (f > 0) {
                g.setColor(new Color(255, 100, 150));
                int dp = f;
                if (startFret != 0) {
                    dp = f - startFret + 1;
                }
                g.fillOval(gridX + (5 - s) * stepW - 5, gridY + dp * stepH - stepH / 2 - 5, 10, 10);
            }
        }
    }

    void drawPixelCloud(Graphics g, int x, int y) {
        g.setColor(colCloud);
        int p = 5;
        g.fillRect(x + p * 2, y, p * 4, p);
        g.fillRect(x + p, y + p, p * 6, p);
        g.fillRect(x, y + p * 2, p * 8, p * 2);
        g.fillRect(x + p, y + p * 4, p * 6, p);
    }

    void startMic() {
        new Thread(() -> {
            try {
                AudioFormat format = new AudioFormat(44100, 16, 1, true, false);
                TargetDataLine line = (TargetDataLine) AudioSystem.getLine(new DataLine.Info(TargetDataLine.class, format));
                line.open(format);
                line.start();

                byte[] buffer = new byte[2048];
                while (true) {
                    int read = line.read(buffer, 0, buffer.length);
                    int crossings = 0;
                    long ampSum = 0;

                    for (int i = 0; i < read - 2; i += 2) {
                        short s1 = (short) ((buffer[i + 1] << 8) | (buffer[i] & 0xff));
                        short s2 = (short) ((buffer[i + 3] << 8) | (buffer[i + 2] & 0xff));
                        ampSum += Math.abs(s1);
                        if (s1 > 0 && s2 <= 0) crossings++;
                    }

                    currentFreq = (crossings / 2.0) * (44100.0 / (read / 2.0));
                    currentAmp = (int)(ampSum / (read / 2));

                    if (!isMuted) {
                        if (gameState == 2) {
                            if (currentAmp > minAmplitude && lastAmp <= minAmplitude) {
                                detectedPeakFreq = (int) currentFreq;
                            }
                            lastAmp = currentAmp;
                            int historyVal = (currentAmp > minAmplitude) ? (int) currentFreq : 0;
                            freqHistory.add(0, historyVal);
                            if (freqHistory.size() > 60) freqHistory.remove(60);
                        }

                        if (currentAmp > minAmplitude) {
                            int newPotentialY = targetY;
                            if (currentFreq > freqHigh - 50) {
                                newPotentialY = 70;
                            } else if (currentFreq > freqMidHigh - 50) {
                                newPotentialY = 160;
                            } else if (currentFreq > freqMid - 50) {
                                newPotentialY = 250;
                            } else if (currentFreq > freqMidLow - 50) {
                                newPotentialY = 340;
                            } else if (currentFreq > 60) {
                                newPotentialY = 430;
                            }

                            if (newPotentialY == potentialTargetY) {
                                stabilityCounter++;
                            } else {
                                potentialTargetY = newPotentialY;
                                stabilityCounter = 0;
                            }

                            if (stabilityCounter >= 2) {
                                targetY = potentialTargetY;
                            }
                        }
                    }
                    Thread.sleep(10);
                }
            } catch (Exception ex) {
                ex.printStackTrace();
            }
        }).start();
    }
    @Override
    public void actionPerformed(ActionEvent e) {
        if (gameState == 1 && !isGameOver) {


            if (isMuted) {
                velocity += gravityConstant;
                birdY += (int)velocity;
            } else {

                double diff = targetY - birdY;
                double diff1 = targetY - birdY;

                if (Math.abs(diff1) < 2) {
                    birdY = targetY;
                } else {
                    birdY += (int)(diff * 0.12);
                }
                velocity = 0;
            }


            for (int i = 0; i < 3; i++) {
                pipesX[i] -= 4;

                if (pipesX[i] == birdX) score++;

                if (birdX + 35 > pipesX[i] && birdX < pipesX[i] + pipeWidth) {
                    int gapCenter = pipesGapY[i];
                    int gapHalf = 125; // Окно пролета
                    if (birdY < gapCenter - gapHalf || birdY + 30 > gapCenter + gapHalf) {
                        isGameOver = true;
                    }
                }

                if (pipesX[i] < -100) {
                    int maxX = 0;
                    for (int j = 0; j < 3; j++) {
                        if (pipesX[j] > maxX) maxX = pipesX[j];
                    }
                    pipesX[i] = maxX + 400;
                    int[] possibleY = {70, 160, 250, 340, 430};
                    pipesGapY[i] = possibleY[rnd.nextInt(5)];
                }
            }

            if (birdY > 580 || birdY < -50) isGameOver = true;


            for (int i = 0; i < numClouds; i++) {
                cloudsX[i] -= cloudsSpeed[i];
                if (cloudsX[i] < -100) {
                    cloudsX[i] = 850;
                    cloudsY[i] = rnd.nextInt(350) + 30;
                }
            }
        }
        repaint();
    }
    public static void main(String[] args) {
        JFrame f = new JFrame("flappybird");
        f.add(new Main());
        f.setSize(800, 600);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setLocationRelativeTo(null);
        f.setResizable(false);
        f.setVisible(true);
    }
}
