Check if cycle is present in a Linked list
Driver function:
bool cyclePresent(Node *node)
{
    unordered_set<Node*> s;
    while(node!=NULL)
    {
        if(s.find(node)!=s.end())
        return true;//(LL has cycle);

        s.insert(node);
        node=node->next;
    }
    return false;//(LL doesnt have a cycle in it);
}