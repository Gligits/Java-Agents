# JADE (Java Agent Development Framework)
JADE is a framework for developing multi-agent systems in Java. It simplifies the implementation of agents that can communicate and cooperate to perform tasks. Each agent runs as an independent thread and can perform specific behaviors.
## Agents
Communicate with other agents.
Make decisions based on its goals and environment.
Perform actions based on behaviors.

Agents are created by extending the Agent class in JADE and overriding the `setup()` method. 
The `setup()` method is where you initialize the agent and define its behaviors.

    import jade.core.Agent;

    public class MyAgent extends Agent {
    protected void setup() {
        System.out.println("Hello, I am " + getLocalName());
    }
    }
Note that to run this, you'll need to introduce the arguments through the RUN CONFIGURATIONS as shown here :
**-flag identifier:classname**
In this case you can use : **-gui GLIGITS:YOURCLASSNAME**

## Behaviors

Behaviors in JADE define the actions an agent can perform. 
There are different types of behaviors you can use, depending on the task:

- SimpleBehavior: Basic behavior executed once. It involves overriding the action() and done() methods.
- CyclicBehavior: Repeats indefinitely (useful for ongoing tasks).
- OneShotBehavior: Executes its action() method only once and then finishes.
- SequentialBehavior: Allows you to add multiple behaviors that execute one after another.
- ParallelBehavior: Executes multiple behaviors concurrently.

### Creating a Behavior (implementation)
To create a behavior, you extend one of the behavior classes (Behaviour, CyclicBehaviour, etc.) and override the action() and done() methods

    import jade.core.behaviours.Behaviour;

    public class MyBehavior extends Behaviour {
    int step = 0;

    public void action() {
        switch (step) {
            case 0:
                System.out.println("Performing step 0");
                step++;
                break;
            case 1:
                System.out.println("Performing step 1");
                step++;
                break;
            case 2:
                System.out.println("Performing step 2");
                step++;
                break;
        }
    }

    public boolean done() {
        return step == 3;
    }
    }
#### Adding Behaviors to an Agent
  Behaviors are added to an agent using the addBehaviour() method in the setup() method
  
    import jade.core.Agent;

    public class MyAgent extends Agent {
    protected void setup() {
        System.out.println("Hello, I am " + getLocalName());
        addBehaviour(new MyBehavior()); // Adding a behavior to the agent
    }
    }

Note : while doing an execution like this : 

    import jade.core.Agent;

    public class Agent2 extends Agent {
	
	public void setup(){
			System.out.println("Hello world my name is " + getLocalName()); addBehaviour(new B1());
			}
	public static void main(String[] args) {
		String [] jadeArg = new String [2];
		StringBuffer SbAgent = new StringBuffer();
		SbAgent.append("S1:Agent2;");
		SbAgent.append("S2:Agent2;");
		SbAgent.append("S3:Agent2;");


		jadeArg[0]="-gui";
		jadeArg[1]=SbAgent.toString();
		jade.Boot.main(jadeArg);
		}
    }

An inversion might occur due to the way the JADE platform processes and schedules agents. When you launch multiple agents in JADE, the execution order isn't strictly guaranteed to follow the order in which the agents are listed. JADE manages agents as separate threads, and the operating system schedules these threads for execution, leading to potential variations in the order of output.
Another thing that you might have noticed is that this execution contains the arguments here 

    jadeArg[0]="-gui";
    jadeArg[1]=SbAgent.toString();
    jade.Boot.main(jadeArg);

This means you won't need to introduce them when you want to run it, so you can directly click on RUN!
