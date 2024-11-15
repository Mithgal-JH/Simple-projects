//Reverse
node* revers(node* cur, node* prev)
{
    if (cur)
    {
        node *cr_next=cur->next;
        cur->next = prev;

        if (cr_next == NULL)
            return cur;
        revers(cr_next, cur);
    }
}
//Is_palindrome?
bool IsPalindrome()
{
    if (!head)
    {
        return true;
    }
    node* slow = head;
    node* fast = head;
    while (fast->next)
    {
        slow = slow->next;
        fast = fast->next;
        if (fast->next)
            fast = fast->next;
    }
    node* newhead = revers(slow, NULL);
    bool palindrome = true;
    while (palindrome && newhead && head)
    {
        if (newhead->data != head->data)
        {
            palindrome = false;
        }
        newhead = newhead->next;
        head = head->next;
    }
    return palindrome;
}
