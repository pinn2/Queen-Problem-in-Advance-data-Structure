/* Queen-Problem-in-Advance-data-Structure
   Queen problem(Advance Data structure) solving using Java Swing which provide 
   GUI System application to solve this problem as Game.
   enjoy queen game
   
   JAVA SWING GUI APPLICATION.
  */
  
  import java.awt.event.*;  
  import javax.swing.*;
  import java.io.*;  
  
public class Queen implements ActionListener{ 
    static int N,q=0;
    int x,y;
    JFrame f;  
    JButton b[][]= new JButton[N][N];  
    Queen()
       {  
            
             f=new JFrame(); 
             f.setLayout(new java.awt.GridLayout(N,N));
             
             for(int i=0;i<N;i++){
                 for(int j=0;j<N;j++){
                   b[i][j]= new JButton();
                   f.add(b[i][j]);
                   b[i][j].addActionListener(this);
                }
              }
             f.setSize(300,300);  
             f.setVisible(true);
               
       }  
    void rbd(int tx,int ty){
            while(tx<(N-1) && ty<(N-1)){
                 tx++;ty++;
                 b[tx][ty].setEnabled(false);
             }
       }
   void lbd(int tx,int ty){
            while(tx<(N-1) && ty>0){
                 tx++;ty--;
                 b[tx][ty].setEnabled(false);
             }
       }
  void lad(int tx,int ty){
            while(tx>0 && ty>0){
                 tx--;ty--;
                 b[tx][ty].setEnabled(false);
             }
       }
  void rad(int tx,int ty){
            while(tx>0 && ty<(N-1)){
                 tx--;ty++;
                 b[tx][ty].setEnabled(false);
             }
       }
  void ln(int tx,int ty){
            for(int i=0;i<N;i++){
                 b[tx][i].setEnabled(false);
                 b[i][ty].setEnabled(false);
             }
       }
    public void actionPerformed(ActionEvent obj) {
             for(int i=0;i<N;i++){
                 for(int j=0;j<N;j++){
                    if(obj.getSource()== b[i][j]){
                           x=i;y=j;
                           b[i][j].setText("Q");
                           q++;
                           System.out.println("YOU PUT NUMBER OF QUEENS: "+q);
                           rbd(x,y);
                           lbd(x,y);
                           lad(x,y);
                           rad(x,y);
                           ln(x,y);
                          }
                  }
               }
          }
    public static void main(String[] args) {  
   
    Console in = System.console();
    N= Integer.parseInt(in.readLine());
    new Queen();
   }  
}  
