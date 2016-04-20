# sb_refact

INSTALLING AND RUNNING THE PLUGIN WITH THE EXAMPLE: **MOVING LOCAL VARIABLES**
---------------------

1. _git clone_ link of the project
2. on eclipse, _import_ --> _existing projects into workspace_ --> then choose the project
3. right click on the project and then choose _debug as_ --> _eclipse application_
4. Once the second eclipse is launched, Import any project in that new workspace of that second eclipse instance (you can for instance create a new project example.)
5. right-click on any class and see a custom entry in the contextual menu: "Ast article: Move Declaration" (the action to detect contradicting variable declarations and to move them to their correct place)


So now almost everything is in place to test those AST manipulation.

One last thing: create a Java Unit compilation able to highlights those variable declarations rewrites.

Create in your imported project (whatever it is) a package test, with the class:

{
    package test;
    
    public class Test {
    
        static {
        	int i = 2;
        	System.out.println("test");
        	System.out.println(i);
        }
    
    }
}

Right-click on that class and select "Ast article: Move Declaration": see the source being instantly rewritten as:

{
    
    package test;
    
    public class Test {
    
        static {
        	System.out.println("test");
        	int i = 2;
        	System.out.println(i);
        }
    
    }
}

to know more about the AST's code, take a look at [this article](http://www.eclipse.org/articles/Article-JavaCodeManipulation_AST/) about the AST!
