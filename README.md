import java.util.Scanner;

public class amerges {
	
	void partition(int arr[] , int p , int r){		
		if(p<r){
			 int q=(p+r)/2;
			 partition(arr,p,q);
			 partition(arr,q+1,r);
			 partition(arr,p,q,r);			 
		}
	}
	
	void merge(int arr[] ,int p,int q,int r){
  
		int n1,n2,i,j,k;
		int arrl[] = new int[25];//left array
		int arrr[] = new int[25];//right array
	
		n1=q-p+1;
		n2=r-q;		
		
		for(i=1;i<n1+1;i++){
			arrl[i] = arr[p+i-1];
		}
		
		for(j=1;j<n2+1;j++){
			arrr[j] = arr[q+j];
		}
		
		arrl[n1+1]=60000;
		arrr[n2+1]=60000;
		
		i=1;
		j=1;
		
		for(k=p;k<r+1;k++){
			if(arrl[i]<=arrr[j]){
				arr[k]=arrl[i];
				i=i+1;
			}
			else{
				arr[k]=arrr[j];
				j=j+1;
			}
		}
    
	}
	
	public static void main(String args[]){		
		
		int num,i;
		int arrs[] = new int[50];//Sorted list
		
		Scanner sys = new Scanner (System.in);
		
		amerges ob = new amerges();
		
		System.out.print("Enter The Size of the List :");
		num = sys.nextInt();
		
		System.out.println("Enter the data in the List :");
		for(i=1;i<num+1;i++){
			arrs[i]=sys.nextInt();
		}
    
		ob.partition(arrs,1,num);
		
		System.out.println("The Sorted List is :");
		for(i=1;i<num+1;i++){
			System.out.print(arrs[i]+" ");
		}
	}

}
