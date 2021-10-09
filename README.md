# Java-Roleta

Este é um programa básico onde não foram consideradas todas as hipóteses do jogo.
Também não foi efetuado o tratamento de erros por ser apenas um exemplo.

### Para a execução deste jogo em Java:

1. Criação de imagens e gif com o prgrama GIMP,
2. Código de lógica:
  Sortear números aleatórios,
  Verificação se número escolhido é igual ao sorteado,
  Compatibilização do número sorteado com a imagem gif, e alteração de imagens em tempo de execução,
3. Criar uma Janela,
4. Inserir caixas de leitura de texto,
5. Inserir textos,
6. Inserir imagens,
7. Inserir botões,
8. Criar ações para botões,
9. Utilização da Class Thread para execução simultânea de métodos.

O jogo pode ser jogado executando o arquivo Roleta.jar 
(Poderá ser necessário marcar o mesmo arquivo como executável nas permissões do computador)

Sugestões são bem vindas!

Código:

package com.joaonunodev;

import java.awt.Font;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JTextField;

public class Janela extends JFrame implements ActionListener {
	
	JLabel lRoleta = new JLabel();        //onde vai ser inserida a Roleta
	JButton jb = new JButton("Rolar!");
	JButton jbSair = new JButton("Sair");
	JTextField nEscolhido = new JTextField(50);
	JTextField vAposta = new JTextField(50);
	JLabel escolherNumero = new JLabel("Escolha um número: ");
	JLabel escolherAposta = new JLabel("Qual o valor da aposta? ");
	JLabel resultado = new JLabel("Resultado: ");
	JLabel premio = new JLabel();
	JLabel dev = new JLabel("joaonunodev");
	
	Font grande = new Font("Arial", Font.BOLD,20);
	
	int nS; //numero sorteado
	int numeroEscolhido;
	int valorAposta;
	int valorGanho;
	
	
	// Método que define a ação do botão:
	public void actionPerformed(ActionEvent e) {
		
		if (e.getSource()==jb) {
			new Jogo().start();
			}
		
		if (e.getSource()==jbSair) {
			System.exit(0);
			}   
	}
	
	
	public void mudarImagem(String nome) {
		
		lRoleta.setIcon(new ImageIcon(getClass().getResource(nome)));
		
	}
	
	
	public class Jogo extends Thread{
		
		public void run() {
			premio.setText("");
			nS = (int)(Math.random()*37);
			int num = (int) (Math.random()*3);
			int n;
			numeroEscolhido = Integer.parseInt(nEscolhido.getText());
			valorAposta = Integer.parseInt(vAposta.getText());
			
			switch(nS) {
			case 0 : n = 0; break;
			case 32: n = 1; break;
			case 15: n = 2; break;
			case 19: n = 3; break;
			case 4 : n = 4; break;
			case 21: n = 5; break;
			case 2 : n = 6; break;
			case 25: n = 7; break;
			case 17: n = 8; break;
			case 34: n = 9; break;
			case 6 : n = 10; break;
			case 27: n = 11; break;
			case 13: n = 12; break;
			case 36: n = 13; break;
			case 11: n = 14; break;
			case 30: n = 15; break;
			case 8 : n = 16; break;
			case 23: n = 17; break;
			case 10: n = 18; break;
			case 5 : n = 19; break;
			case 24: n = 20; break;
			case 16: n = 21; break;
			case 33: n = 22; break;
			case 1 : n = 23; break;
			case 20: n = 24; break;
			case 14: n = 25; break;
			case 31: n = 26; break;
			case 9 : n = 27; break;
			case 22: n = 28; break;
			case 18: n = 29; break;
			case 29: n = 30; break;
			case 7 : n = 31; break;
			case 28: n = 32; break;
			case 12: n = 33; break;
			case 35: n = 34; break;
			case 3 : n = 35; break;
			case 26: n = 36; break;
			default: n = 100; break;
			}
			
			mudarImagem("anim.gif");
			try {sleep(4200*(1+num) + n*117);} catch(Exception erro) {}
			
			mudarImagem(nS + ".png");
			JOptionPane.showMessageDialog(null, "numero sorteado: " + nS);
			
			if (nS == numeroEscolhido) {
				valorGanho = 36 * valorAposta;
				premio.setText("Ganhou!! \n" + valorGanho);
			} else {
				premio.setText("Você perdeu!!");
			}
		}
	}
	
	
	public Janela() {
		
		jb.addActionListener(this);
		jbSair.addActionListener(this);
		
		setTitle("Jogo da Roleta");
		setSize(800, 800);
		setVisible(true);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setLocationRelativeTo(null);
		setResizable(true);
		
		setLayout(null);
		jb.setBounds(350, 600, 100, 60);
		jbSair.setBounds(350, 680, 100, 60);
		lRoleta.setBounds(125, 15, 570, 570);
		nEscolhido.setBounds(100, 630, 150, 30);
		vAposta.setBounds(100, 710, 150, 30);
		escolherNumero.setBounds(100, 600, 200, 25);
		escolherAposta.setBounds(100, 680, 200, 25);
		resultado.setBounds(550, 600, 200, 25);
		premio.setBounds(550, 650, 200, 25);
		dev.setBounds(550, 40, 200, 25);
		
		
		add(jb);
		add(jbSair);
		add(lRoleta);
		add(nEscolhido); //JTextField
		add(vAposta); //JTextField
		add(escolherNumero); //JLabel("Escolha um número: ")
		add(escolherAposta); // JLabel("Qual o valor da aposta? ")
		add(resultado); //JLabel
		add(premio); //JLabel
		add(dev);
		premio.setFont(grande);
		
		
		mudarImagem("vazio.png");
	
	}
}
