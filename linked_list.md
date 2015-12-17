#### linked list


    #define TSIZE 45
    struct film{
	    char title[TSIZE];
	    int rating;
	    struct file *next;
    };
    struct film *head;
