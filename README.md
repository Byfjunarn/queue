#queue







#include <stdio.h>
#include <stdlib.h>
#include <queue.h>
#include <list_2cell.h>

-------------------------------------------------------------------------------------
void testAx1IsEmpty()
{
    printf("Testing axiome 1 (if queue_empty produces an empty queue)...\n");
    
    queue *q = queue_empty();
    queue_setMemHandler(q, free);
    
    if(queue_isEmpty(q) != true)
    {
        printf("ERROR! queue_is_empty(q) should return true\n");
        printf("Returned %s", queue_isEmpty(q) ? "true" : "false");
        exit(1);
    }
    else if(queue_isEmpty(q) == true)
    {
        printf("Test successful!\n");
    }

    queue_free(q);
}

void testAx2IsNotEmptyAfterEnqueue()
{
    printf("Testing Axiome 2 (if Enqueue makes queue !empty)\n");
    
    queue *q = queue_empty();
    queue_setMemHandler(q, free);
    int d = 5;
    int *value = malloc(sizeof(int));
    *value = d;
    
    queue_enqueue(q, value);

    if(queue_isEmpty(q) == true)
    {
        printf("ERROR! queue_is_empty(q) should return false\n");
        printf("Returned %s", queue_isEmpty(q) ? "true" : "false");
        exit(1);
    }
    
    else if(!queue_isEmpty(q))
    {
        printf("Test successful!\n");
    }
    
    queue_free(q);
}

void testAx3OneDequeueWithOneValueInQueue()
{
    printf("Testing Axiome 3 (if Dequeue makes queue empty again)\n");
    
    queue *q = queue_empty();
    queue_setMemHandler(q, free);
    int d = 5;
    int *value = malloc(sizeof(int));
    *value = d;
    
    queue_enqueue(q, value);
    
    queue_dequeue(q);
    
    if(queue_isEmpty(q) == true)
    {
        printf("Test successful\n");
    }
    
    else 
    {
        printf("ERROR! queue_is_empty(q) should return True\n");
        printf("Returned %s", queue_isEmpty(q) ? "true" : "false");
        exit(1);
    }
    
    
    queue_free(q);
}


/*void testEnqueue()

 * om inte(IsEmpty (q)) så Dequeue (Enqueue (v,q)) är Enqueue (v, Dequeue (q))
 * 
 * 
void testDequeue()

void testIsLongestQueueAlwaysFirst()*/



int main(void)
{
    testAx1IsEmpty();
    testAx2IsNotEmptyAfterEnqueue();
    testAx3OneDequeueWithOneValueInQueue();
    /*void testEnqueue();
    void testDequeue();
    void testIsLongestQueueAlwaysFirst();*/
    return 0;
}
