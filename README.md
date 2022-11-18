# nev
//C # Программа для реализации траверса дерева двоичного поиска – Preorder, InOrder &
//Postorder. В этой статье мы узнаем: Binary Search Tree Traversal в C#. Бинарный поиск
//дерева Traversal: Вы можете узнать, как реализовать Binary search Tree в C # и
//вставить узлы в BST здесь. B двоичном дереве поиска используются три метода пересечения: порядок, предварительный заказ и постзаказ.
//Обход порядка посещает все узлы в BST в порядке возрастания значений ключа узла.
//Обход предзаказа сначала посещает корневой узел, за которым следуют узлы в поддеревьях под левым дочерним элементом корня, с последующими узлами в поддеревьях под правым //дочерним элементом корня
//Постод пересечения, метод сначала повторяется над левыми поддеревьями, а затем над правыми поддеревьями.

using System;

class Node
{
    public int item;
    public Node left;
    public Node right;
    public void display()
    {
        Console.Write("[");
        Console.Write(item);
        Console.Write("]");
    }
}
class Tree
{
    public Node root;
    public Tree()
    {
        root = null;
    }
    public Node ReturnRoot()
    {
        return root;
    }
    public void Insert(int id)
    {
        Node newNode = new Node();
        newNode.item = id;
        if (root == null)
            root = newNode;
        else
        {
            Node current = root;
            Node parent;
            while (true)
            {
                parent = current;
                if (id < current.item)
                {
                    current = current.left;
                    if (current == null)
                    {
                        parent.left = newNode;
                        return;
                    }
                }
                else
                {
                    current = current.right;
                    if (current == null)
                    {
                        parent.right = newNode;
                        return;
                    }
                }
            }
        }
    }
    public void Preorder(Node Root)
    {
        if (Root != null)
        {
            Console.Write(Root.item + " ");
            Preorder(Root.left);
            Preorder(Root.right);
        }
    }
    public void Inorder(Node Root)
    {
        if (Root != null)
        {
            Inorder(Root.left);
            Console.Write(Root.item + " ");
            Inorder(Root.right);
        }
    }
    public void Postorder(Node Root)
    {
        if (Root != null)
        {
            Postorder(Root.left);
            Postorder(Root.right);
            Console.Write(Root.item + " ");
        }
    }
}
class Program
{
    static void Main(string[] args)
    {
        Tree BST = new Tree();
        BST.Insert(30);
        BST.Insert(35);
        BST.Insert(57);
        BST.Insert(15);
        BST.Insert(63);
        BST.Insert(49);
        BST.Insert(89);
        BST.Insert(77);
        BST.Insert(67);
        BST.Insert(98);
        BST.Insert(91);
        Console.WriteLine("Inorder Traversal : ");
        BST.Inorder(BST.ReturnRoot());
        Console.WriteLine(" ");
        Console.WriteLine();
        Console.WriteLine("Preorder Traversal : ");
        BST.Preorder(BST.ReturnRoot());
        Console.WriteLine(" ");
        Console.WriteLine();
        Console.WriteLine("Postorder Traversal : ");
        BST.Postorder(BST.ReturnRoot());
        Console.WriteLine(" ");
        Console.ReadLine();
    }
}
