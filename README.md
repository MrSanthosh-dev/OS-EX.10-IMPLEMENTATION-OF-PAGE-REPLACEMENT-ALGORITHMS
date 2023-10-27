## OS-EX.10-IMPLEMENTATION-OF-PAGE-REPLACEMENT-ALGORITHMS
## 1.PAGE REPLACEMENT ALGORITHM-(FIFO)
## Aim:
To write a C program to implement Page Replacement technique using FIFO.
## Algorithm:
1. Start the program.
2. Get the number of pages and their sequence from the user
3. Get the number of available page frames from the user.
4. In FIFO, on the basics of first in first out, replace the pages respectively, then find number of page faults occurred.
5. Compare all frames with incoming page-
6. If the incoming page is already available in page frame, set the match flag to indicate ‘no need of page replacement’.
7. If the incoming page is not available in all frames, then remove the page which is loaded into the memory long back and give space for new incoming page.
8. Increment the ‘number of Page faults counter
9. Print the number of page faults.
10. Stop the program.
## Program:
```
#include <stdio.h>
int main() {
    int i, j, n, a[50], frame[10], no, k, avail, count = 0;

    printf("Enter the no.of pages:\n");
    scanf("%d", &n);
    printf("Enter the page number:\n");
    for (i = 1; i <= n; i++)
        scanf("%d", &a[i]);
    printf("Enter the no.of frames: ");
    scanf("%d", &no);

    for (i = 0; i < no; i++)
        frame[i] = -1;
    j = 0;
    printf("Ref string\t Page Frames\n");

    for (i = 1; i <= n; i++) {
        printf("%d\t\t\t", a[i]);
        avail = 0;
        for (k = 0; k < no; k++)
            if (frame[k] == a[i])
                avail = 1;

        if (avail == 0) {
            frame[j] = a[i];
            j = (j + 1) % no;
            count++;

            for (k = 0; k < no; k++)
                printf("%d\t", frame[k]);
        }
        printf("\n");
    }

    printf("\nPage Fault Is %d\n", count);
    return 0;
}
```
## Output:
![image](https://github.com/MrSanthosh-dev/OS-EX.10-IMPLEMENTATION-OF-PAGE-REPLACEMENT-ALGORITHMS/assets/117916573/0f253854-0dd5-44d2-82b3-9535b1805394)

## Result:
Thus the implementation of FIFO page replacement is successfully executed.

## 2.PAGE REPLACEMENT ALGORITHM-(LRU)
## Aim:
To write a C program to implement Page Replacement technique using LRU.
## Algorithm:
1. Start the program
2. Get the number of pages and their sequence from theuser
3. Get the number of available page frames from theuser.
4. In LRU replace the page that has not been used for the longest period oftime.
5. Compare all frames with incoming page-
6. If the incoming page is already available in page frame, set the match flag to
indicate ‘no need of page replacement’.
7. If the incoming page is not available in all frames, then remove the page which
has not been used for the longest period oftime.
8. Increment the ‘number of Page faults’ counter
9. Print the number of page faults.
10. Stop the program.
## Program:
```
#include <stdio.h>
int main()
{
    int q[20], p[50], c = 0, c1, d, f, i, j, k = 0, n, r, t, b[20], c2[20];
    printf("Enter no of pages: \n");
    scanf("%d", &n);
    printf("Enter the reference string: \n");
    for (i = 0; i < n; i++)
    {
        scanf("%d", &p[i]);
    }
    printf("Enter no of frames: \n");
    scanf("%d", &f);
    q[k] = p[k];
    printf("%d\n", q[k]);
    c++;
    k++;
    for (i = 1; i < n; i++)
    {
        c1 = 0;
        for (j = 0; j < f; j++)
        {
            if (p[i] != q[j])
            {
                c1++;
            }
        }
        if (c1 == f)
        {
            c++;
            if (k < f)
            {
                q[k] = p[i];
                k++;
                for (j = 0; j < k; j++)
                {
                    printf("\t%d", q[j]);
                }
                printf("\n");
            } else 
            {
                for (r = 0; r < f; r++)
                {
                    c2[r] = 0;
                    for (j = i - 1; j >= 0; j--)
                    {
                        if (q[r] != p[j])
                            c2[r]++;
                        else
                            break;
                    }
                }
                for (r = 0; r < f; r++)
                {
                    b[r] = c2[r];
                }
                for (r = 0; r < f; r++)
                {
                    for (j = r; j < f; j++)
                    {
                        if (b[r] < b[j])
                        {
                            t = b[r];
                            b[r] = b[j];
                            b[j] = t;
                        }
                    }
                }
                for (r = 0; r < f; r++)
                {
                    if (c2[r] == b[0])
                        q[r] = p[i];
                    printf("\t%d", q[r]);
                }
                printf("\n");
            }
        }
    }
    printf("\nThe number of page faults is %d", c);
    return 0;
}
```
## Output:
![image](https://github.com/MrSanthosh-dev/OS-EX.10-IMPLEMENTATION-OF-PAGE-REPLACEMENT-ALGORITHMS/assets/117916573/c4efec98-ccca-4729-b449-46edb05d6f35)

## Result:
Thus the implementation of LRU page replacement is successfully executed.

## 3.PAGE REPLACEMENT ALGORITHM-(OPR)
## Aim:
To write a C program to implement Page Replacement technique using OPR
## Algorithm:
1. Start the program.
2. Take the input of pages as an array.
3. Look for the page allocated is present in near future, if no then replace that page in the memory with new page,
4. If page already present increment hit, else increment miss.
5. Repeat till we reach the last element of the array.
6. Print the number of hits and misses.
7. Stop the program.
## Program:
```
#include <stdio.h>
int main()
{
    int i, j, n, a[50], frame[10], no, k, avail, count = 0;
    printf("Enter the no.of pages:\n");
    scanf("%d", &n);
    printf("Enter the page number:\n");
    for (i = 0; i < n; i++)
    {
        scanf("%d", &a[i]);
    }

    printf("Enter the no.of frames:\n");
    scanf("%d", &no);
    for (i = 0; i < no; i++)
    {
        frame[i] = -1;
    }
    j = 0;
    printf("ref string\t page frames\n");
    for (i = 0; i < n; i++)
    {
        printf("%d\t\t", a[i]);
        avail = 0;
        for (k = 0; k < no; k++)
        {
            if (frame[k] == a[i])
            {
                avail = 1;
            }
        }
        if (avail == 0)
        {
            frame[j] = a[i];
            j = (j + 1) % no;
            count++;
            for (k = 0; k < no; k++)
            {
                printf("%d\t", frame[k]);
            }
        }
        printf("\n");
    }
    printf("Page Fault Is %d", count);
    return 0;
}
```
## Output:
![image](https://github.com/MrSanthosh-dev/OS-EX.10-IMPLEMENTATION-OF-PAGE-REPLACEMENT-ALGORITHMS/assets/117916573/88387ec3-8605-406c-bee3-18b7055c20c0)

## Result:
Thus the implementation of OPR page replacement is successfully executed.
