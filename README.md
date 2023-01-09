//# merge-sort-cpp-using-recursion
//merge sort in cPP using recursion 


#include <iostream>
using namespace std;

void merge(int leftsubarray[], int rightsubarray[], int arr[], int n , int m){
    int i =0;
    int j =0;
    int k =0;
    
    while(i<n && j<m){
        if(leftsubarray[i] <= rightsubarray[j]){
            arr[k] = leftsubarray[i];
            i++;
        }else{
            arr[k] = rightsubarray[j];
            j++;
        }
        k++;
    }
    
    while(i<n){
        arr[k] = leftsubarray[i];
        i++;
        k++;
    }
    
    while(j<m){
        arr[k] = rightsubarray[j];
        j++;
        k++;
    }
}

void mergesort(int arr[], int size){
    if(size==0){
        return ;
    }
    if(size==1){
        return ;
    }
    
    int n = size/2;
    int m = size -n;
    
    int leftsubarray[n];
    int rightsubarray[m];
    
    int k =0;
    
    for(int i=0; i<n; i++){
        leftsubarray[i] = arr[k];
        k++;
    }
    
    for(int i =0; i<m; i++){
        rightsubarray[i] = arr[k];
        k++;
    }
    
    mergesort(leftsubarray, n);
    mergesort(rightsubarray, m);
    merge(leftsubarray,rightsubarray,arr,n,m);
}

int main()
{
    int n;
    cin >>n;
    int *arr = new int[n];
    for(int i =0; i<n; i++){
        cin >> arr[i];
    }
    
    for(int i =0; i<n; i++){
        cout<< arr[i] << " ";
    }cout<< endl;
    
    mergesort(arr, n);
    
    cout<<"After Sorting" << endl;
    
    for(int i =0; i<n; i++){
        cout<< arr[i] << " ";
    }cout<< endl;
    

    return 0;
}

