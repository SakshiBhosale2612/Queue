# Queue
Program for Queue using LinkedList in java

package i1.sakshi;

import java.util.Scanner;

public class Queue {

    public static class Node{
        int data;
        Node link;
        public Node(){

        }
        public Node(int data){
            this.data= data;
            this.link=null;
        }
    }
    public static class head {
        static int count;
        static Node front;
        static Node rear;
    }
  /*  public static void creatQueue(Queue q){
        Node newnode= new Node();
        head.front=newnode;
        head.rear=newnode;
        head.count=0;
        newnode.link=null;
    }
    */

    public static void enqueue(){
        Node newnode =new Node();
        if(isfull(newnode)==true) {
            System.out.println("        Queue is full!!!!");
        }else {
            Scanner sc = new Scanner(System.in);
            System.out.print("Enter next data to enqueue : ");
            int data = sc.nextInt();
            newnode.data = data;
            if (head.count == 0) {
                head.front = newnode;
                head.rear = newnode;
                head.count = 1;
            } else {
                head.rear.link = newnode;
                head.rear = newnode;
                head.count = head.count + 1;
            }
        }
    }
    public static void dequeue(){
        if(isempty()==true) {
            System.out.println("        Queue is empty!!!!");
        }else {
            System.out.print("Data will be dequeue: " + head.front.data);
            head.count = head.count - 1;
            head.front = head.front.link;
        }
    }
    public static void queuefront(){
        System.out.print("      Queue Front : "+head.front.data);
    }
    public static void queuerear(){
        System.out.print("      Queue Rear : "+head.rear.data);
    }
    public static boolean isempty(){
        boolean a;
        if(head.count==0){
            a=true;
        }else{
            a=false;
        }
        return a;
    }
    public static boolean isfull(Node newnode){
        boolean a;
        if(newnode==null){
            a=true;
        }else{
            a=false;
        }
        return a;
    }
    public static void main(String[] args) {
        Queue q=new Queue();
        int choice;
        do {
            System.out.println("\n1.Enqueue \n2.Dequeue \n3.Queue front \n4.Queue rear ");
            System.out.print("Choose : ");
            Scanner sc = new Scanner(System.in);
            choice = sc.nextInt();
            switch(choice){
                case 1:
                    enqueue();
                    break;
                case 2:
                    dequeue();
                    break;
                case 3:
                    queuefront();
                    break;
                case 4:
                    queuerear();
                    break;

                default:
                    System.out.println("    Invalide choice !!!!");

            }

        }while(choice<5);
    }
}
