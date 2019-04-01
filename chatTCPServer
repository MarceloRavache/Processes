import java.net.*;
import java.io.*;
import java.util.Scanner;

public class ChatTCPServer {
    public static void main (String args[]) {
        try{
            int serverPort = 7896;
            ServerSocket listenSocket = new ServerSocket(serverPort);
            Socket clientSocket = listenSocket.accept();
            Connection c = new Connection(clientSocket);
        } catch(IOException e) {System.out.println("Listen socket:"+e.getMessage());}
    }
}
class Connection extends Thread {
    DataInputStream in;
    DataOutputStream out;
    Socket clientSocket;
    public Connection (Socket aClientSocket) {
        try {
            clientSocket = aClientSocket;
            in = new DataInputStream( clientSocket.getInputStream());
            out =new DataOutputStream( clientSocket.getOutputStream());
            this.start();
        } catch(IOException e) {System.out.println("Connection:"+e.getMessage());}
    }
    public void run(){
        try {
            Scanner entrada = new Scanner(System.in);
            while(true) {
                String data = in.readUTF();
                System.out.println("Cliente: "+data);
                String linha = entrada.nextLine();
                out.writeUTF(linha);
            }
        }catch (EOFException e){System.out.println("EOF:"+e.getMessage());
        } catch(IOException e) {System.out.println("readline:"+e.getMessage());
        } finally{ try {clientSocket.close();}catch (IOException e){/*close failed*/}}


    }
}
