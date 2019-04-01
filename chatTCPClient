import java.net.*;
import java.io.*;
import java.util.Scanner;

public class ChatTCPClient {
    public static void main (String args[]) {
        // java conectar ip1
        Socket s = null;
        try{
            Scanner entrada = new Scanner(System.in);
            int serverPort = 7896;
            s = new Socket(args[0], serverPort);
            DataInputStream in = new DataInputStream( s.getInputStream());
            DataOutputStream out =new DataOutputStream( s.getOutputStream());

            while(true){
                String linha = entrada.nextLine();
                out.writeUTF(linha);
                String data = in.readUTF();
                System.out.println("Servidor: "+data);
            }
        }catch (UnknownHostException e){System.out.println("Socket:"+e.getMessage());
        }catch (EOFException e){System.out.println("EOF:"+e.getMessage());
        }catch (IOException e){System.out.println("readline:"+e.getMessage());
        }finally {if(s!=null) try {s.close();}catch (IOException e){System.out.println("close:"+e.getMessage());}}
    }
}
