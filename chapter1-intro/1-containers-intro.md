# 1. Introduction to Containers:  
## 1.1 Software before Containers: Like Sharing Recipes

**It is all about Apps (more precisely Apps distribution) !**  

> Imagine you've just baked the most delicious cookies using a special recipe. You want your friend to taste them too. Instead of giving them the actual cookies, you hand them the recipe. This recipe lists ingredients like chocolate chips, flour, sugar, and eggs.  

![](../images/cookies1.png)

>Your friend, excited, follows the recipe. But when they make the cookies, they don't taste quite the same. Perhaps they used a different brand of chocolate or maybe their oven temperature was off.

![](../images/cookies2.png)

That's how software used to work:

* Sharing Recipes:  
  Before containers, sharing software was like giving someone a recipe. They got instructions on how to set it up, meaning they had to gather all the "ingredients" (software parts) and hope they got them right.  

* Different Kitchens, Different Results:  
  Everyone's computer is a bit different, much like kitchens. Even if two people had the same software "recipe", the final software might behave differently because of those small variations.

## 1.2 Introducing Containers: The Full Cookie Box

>Now, think about a magical cookie box. This isn't just any box. Inside it, there are already baked cookies, a mini-oven to warm them, and even a small cup of milk on the side. Everything is self-contained. You hand this box to your friend, and when they open it, they get the exact same delicious experience you intended. No variations, no unexpected surprises.

![](../images/cookies3.png)

That's what containers do for software:  

* Complete Package:  
  Containers don't just share the "recipe" of software. They pack the whole experience - the software, all its dependencies, and even its environment settings.  

* Consistent Experience Everywhere:  
  With containers, software behaves the same no matter where it's run. It's like giving someone the full cookie experience in a box.  

In essence, containers ensure that the delicious "cookie" experience you create is exactly what others get to enjoy, without the hassles of different "kitchen" environments messing things up.  

   

## 1.3 10+ Benefits of Containers  

1. **Consistency:**  
   Containers ensure software runs the same across different environments (e.g., development, testing, production).  

2. **Isolation:**  
   Each container operates independently, so changes or failures in one don't affect others.

3. **Efficiency:**  
   Containers share the same OS kernel, making them lightweight compared to traditional virtual machines.

4. **Portability:**  
   Software packed in a container can be easily moved across cloud providers, on-premises data centers, and developers' local machines.  

5. **Microservices Ready:**  
   Containers are a natural fit for microservice architectures, enabling each service to run in its own environment.  

6. **Resource Efficiency:**  
   With containers, you can run many apps on a single machine, maximizing resource utilization.  

7. **Faster Deployments:**  
   As containers package all dependencies, it reduces the chances of issues during deployment, leading to quicker releases.  

8. **Scalability:**  
   Easily scale up or down based on demand by spinning up more or fewer containers.  

9. **Version Control & Rollback:**
   Containers can be versioned, and rolling back to a previous version is straightforward.  

10. **Easier Debugging & Diagnosis:**  
    Replicate exact production environment locally to diagnose issues.

11. **Immutability:**  
    Containers support the principle of immutability, meaning once they're set, they don't change. New changes necessitate deploying a new container, ensuring consistency.  

12. **Security:**  
    Containers can offer strong isolation boundaries between applications, enhancing security.  

13. **Developer Productivity:**  
    Developers can work in a local environment that matches production, reducing the "it works on my machine" issues.  

14. **Legacy Application Support:**  
    Containerization can breathe new life into old applications by allowing them to run in modern environments without full refactoring.  
   
   
## 1.4. Containers vs. Virtual Machines

![](../images/containers-vs-virtual-machines.jpg)  

>Imagine you're going to a carnival or a trade fair (the computer).  

>VMs are like setting up complete stalls or shops. Each shop has its structure, electricity connection, staff, and products. Setting up each shop takes time, and each shop functions independently.

![](../images/carnival1.png)

>Containers are like booths or tents. They share the carnival's electricity and infrastructure, and they set up faster. Each booth has its products but depends on the carnival's main resources.

![](../images/carnival2.png)   

   
### Virtual Machines (VMs):

--> Complete OS: VMs run a full operating system (including kernel) on top of the host OS. This OS is known as the guest OS.  

--> Resources: VMs have fixed resources. When you create a VM, you allocate specific amounts of RAM, storage, and CPU cores.  

--> Isolation: Each VM is completely isolated. This means the failure or a security breach in one VM doesn't affect others.  

--> Size: VM images are often large because they include a full OS and its binaries.  

--> Booting Time: VMs often have longer boot times since they need to start an entire operating system.  

### Containers:

--> Shared OS: Containers all share the same OS kernel and isolate the application processes from each other.

--> Resources: Containers are more flexible with resources. They can use as much or as little as available and needed.

--> Isolation: Containers are isolated, but they share the same kernel. The isolation is at the process level.

--> Size: Container images are usually smaller since they only need to include the application and its dependencies.

--> Booting Time: Containers start almost instantly since there's no OS to boot.  
