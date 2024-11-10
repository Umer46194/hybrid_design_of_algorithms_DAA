# hybrid_design_of_algorithms_DAA

#include <iostream>
#include <vector>
using namespace std;
void insertionSort(vector<int>& arr, int left, int right) {
    for (int i = left + 1; i <= right; ++i) {
        int key = arr[i];
        int j = i - 1;
        while (j >= left && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

void merge(vector<int>& arr, int left, int mid, int right) {
    int leftSize = mid - left + 1;
    int rightSize = right - mid;

    std::vector<int> leftSub(leftSize), rightSub(rightSize);

    for (int i = 0; i < leftSize; ++i)
        leftSub[i] = arr[left + i];
    for (int j = 0; j < rightSize; ++j)
        rightSub[j] = arr[mid + 1 + j];

    int i = 0, j = 0, k = left;

    while (i < leftSize && j < rightSize) {
        if (leftSub[i] <= rightSub[j]) {
            arr[k] = leftSub[i];
            i++;
        } else {
            arr[k] = rightSub[j];
            j++;
        }
        k++;
    }

    while (i < leftSize) {
        arr[k] = leftSub[i];
        i++;
        k++;
    }

    while (j < rightSize) {
        arr[k] = rightSub[j];
        j++;
        k++;
    }
}

void hybridSort(std::vector<int>& arr, int left, int right, int threshold = 10) {
    if (left < right) {
        if (right - left + 1 <= threshold) {
            insertionSort(arr, left, right);
        } else {
            int mid = left + (right - left) / 2;
            hybridSort(arr, left, mid, threshold);
            hybridSort(arr, mid + 1, right, threshold);
            merge(arr, left, mid, right);
        }
    }
}

int main() {
    vector<int> arr = {38, 27, 43, 3, 9, 82, 10};

    hybridSort(arr, 0, arr.size() - 1);

    cout << "Sorted array: ";
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;

    return 0;
}
