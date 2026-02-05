//Write a C program to check whether a given element is present in an array of elements using linear search.

#include <stdio.h>
int main()
{
	int n, key, i, found = 0;
	int arr[100];

	scanf("%d", &n);

	for (int i = 0; i < n; i++){
		scanf("%d",&arr[i]);
		}

		scanf("%d", &key);

		for (i = 0; i < n; i++)
		{
		  if (arr[i] == key)
		  {
			printf("found at position %d\n", i);
			found = 1;
			break;
		}
	}

	if (found == 0) {
		printf("%d not found\n", key);
		}

		return 0;
}
