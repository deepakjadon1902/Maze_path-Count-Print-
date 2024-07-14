import java.util.*;
public class Main {
    static int cnt=0;
    public static void main(String args[]) {
 
        Scanner sc = new Scanner(System.in); 
        int n1 = sc.nextInt();
        int n2 = sc.nextInt();
    char board[];
    board=new char[100000];
    for(int i=0;i<100000;i++){
        board[i]='0';
    }
     Mazepathcnt(0,0,n1-1,n2-1,board,0);
    Mazepath(0,0,n1-1,n2-1,board,0);
    System.out.print("\n"+cnt);
    }
 
 
 
 
    public static boolean canimove(int row,int col,int enRow,int enCol){
    if(row<=enRow && col<=enCol)
        return true;
    return false;
}
public static boolean Mazepathcnt(int stRow,int stCol,int enRow,int enCol,char board[],int j){
    if(stRow>=enRow && stCol>=enCol){
        cnt++;
        return false;
    }
 
    boolean istrue=canimove(stRow+1,stCol,enRow,enCol);
    if(istrue){
        board[j]='V';
        boolean IsSuccess1=Mazepathcnt(stRow+1,stCol,enRow,enCol,board,j+1);
        if(IsSuccess1){
            return true;
        }
    }
    boolean IsTrue2=canimove(stRow,stCol+1,enRow,enCol);
    if(IsTrue2){
        board[j]='H';
        boolean IsSuccess2=Mazepathcnt(stRow,stCol+1,enRow,enCol,board,j+1);
        if(IsSuccess2){
            return true;
        }
    }
    board[j]='0';
    return false;
 
}
public static boolean Mazepath(int stRow,int stCol,int enRow,int enCol,char board[],int j){
    if(stRow>=enRow && stCol>=enCol){
        for(int i=0;i<j;i++)
            System.out.print(board[i]);
        System.out.print(" ");
        return false;
    }
 
    boolean istrue=canimove(stRow+1,stCol,enRow,enCol);
    if(istrue){
        board[j]='V';
        boolean IsSuccess1=Mazepath(stRow+1,stCol,enRow,enCol,board,j+1);
        if(IsSuccess1){
            return true;
        }
    }
    boolean IsTrue2=canimove(stRow,stCol+1,enRow,enCol);
    if(IsTrue2){
        board[j]='H';
        boolean IsSuccess2=Mazepath(stRow,stCol+1,enRow,enCol,board,j+1);
        if(IsSuccess2){
            return true;
        }
    }
    board[j]='0';
    return false;
 
}
}
