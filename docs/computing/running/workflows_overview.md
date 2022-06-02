# Pros and cons of different workflow managers
Workflow management systems are handy in managing and executing  multistep complex computational tasks in scientific data analysis. While the workflows in general aim to facilitate salient features such as reproducibility, usability and portability, the use of a specific workflow in HPC environment has to used cautiously.  The following table tries to give you a better picture of different workflows in CSC supercomputing environment.


<table>
<tr> <th>   </th> <th> Nextflow </th><th>Snakemake	</th><th> Merlin/Flux	</th><th> Greasy	</th>  <th> HyperQueue	</th><th> FireWorks </th> 
<tr> <th> platform</th> <td>	Groovy/JVM</td><td>	Python	</td><td> Merlin (Python); Flux (Python, C and lua)</td></td><td> <td>	Rust/Python	</td><td> Python</td>
  </tr>
  <tr>
   <th> Number of files created	</th> <td> 
  
 ```diff 
 !! Depends on number
 !of tasks; A folder
 !!! per task
 ```
  </td> <td>
  
  ```diff 
 
  ```
  </td> <td> 
  
 ```diff 
 ! Folder hierarchy 
 ! for tasks, creates
 ! four files per workflow 
 ! item
 ```
 </td>
 <td> 
  
 ```diff 
 ! Depends on the workflow
 ! /jobs executed
 ```
 </td>
 <td> 
  
 ```diff 
 ! In practice there 
 ! are are no  
 ! additional files.
 ```
 </td>
 <td> 
  
 ```diff 
 ! Depends on the 
 ! workflow, at least 
 ! 4 per workflow
 ```
 </td>

   <tr> <th> Number of jobs & job steps created</th>	<td>
      
 ```diff 
 ! It depends on how 
 ! job is submitted 
 ```
 </td>
     <td>
    </td>
 <td> 
  
 ```diff 
 +  With Flux just single
 +  job step
 ```
   </td>
 <td>  
   
 ```diff 
 - creates job steps
 ```
   </td>
 <td>  
   
 ```diff   
 ! Depends on the workflow.
 ! Might be just one job 
 ! step for the whole
 ! workflow. But depends
 ! on the HQ jobs executed
 ```
 </td>
 <td> 
  
 ```diff 
 ! Creates one job step for
 ! each "firetask" (no way 
 ! to "pack" multiple job 
 ! steps)  
 ```
  </td>
  </tr>

 <tr> <th> Easy to set up / which / how many additional services needed</th>	<td>
      
 ```diff 
 + Installation is 
 + easy; no database
 +  depenndencies
 ```
 </td>
 <td>
        
 ```diff      
 + Easy to install 
 + (just pip)
 ```
 </td>
     <td>
        
 ```diff  
 ! Requires at least Redis DB 
 ! for results, optionally 
 ! RabbitMQ for message brokering
 ```
   </td>
 <td>  
   
 ```diff 
 + easy
 ```
   </td>
 <td>  
   
 ```diff   
 + easy  
 ```
 </td>
 <td> 
  
 ```diff 
 + Fireworks is easy to 
 + install (just pip), 
 - but needs MongoDB
 ```
  </td>
</tr>

  <tr> <th> Supports dependencies/conditional execution of steps</th>	<td>
      
 ```diff 
 + Yes
 ```
 </td>
     <td>
        
 ```diff      
 + Yes using check-
 + points,but unclear
 + how while like 
 + conditions can be
 + handled
 ```
 </td>
     <td>
        
 ```diff  
 + Yes, different types of 
 + dependencies, restarts  
 ```
   </td>
 <td>  
   
 ```diff 
 ! simple dependencies
 ```
   </td>
 <td>  
   
 ```diff   
 - Not really 
 ```
 </td>
 <td> 
  
 ```diff 
 + yes
 ```
  </td>
</tr>


 <tr> <th> Execution with containers</th>	<td>
      
 ```diff 
 + Yes
 ```
 </td>
     <td>
        
 ```diff      
 + Yes
 ```
 </td>
     <td>
        
 ```diff  
 + Yes 
 ```
   </td>
 <td>  
   
 ```diff 
 #
 ```
   </td>
 <td>  
   
 ```diff   
 + yes 
 ```
 </td>
 <td> 
  
 ```diff 
 ! FW itself offers no support 
 ! for containers. However, 
 ! actual calculations can be
 ! executed in a container.
 ```
  </td>
</tr>



 <tr> <th> Error recovery strategies</th>	<td>
      
 ```diff 
 + Yes
 ```
 </td>
     <td>
        
 ```diff      
 - No (unclear )
 ```
 </td>
     <td>
        
 ```diff  
 + Yes, can continue workflow 
 + after job crashes. Also 
 + possibility for separate restart  
 ```
   </td>
 <td>  
   
 ```diff 
 - no
 ```
   </td>
 <td>  
   
 ```diff   
 - Depends, but not really. 
 ```
 </td>
 <td> 
  
 ```diff 
 ! Detection, logging and 
 ! option for manual restarting.
 ! In case of failure, FW will 
 ! continue to do all tasks 
 ! that do not depend on the 
 ! failed task
 ```
  </td>
</tr>


 <tr> <th> Supports which ways of parallelization? OpenMP, MPI, mixed</th>	<td>
      
 ```diff 
 + Implicit parallelism
 ! MPI support is available
 ```
 </td>
     <td>
        
 ```diff      
  
 ```
 </td>
     <td>
        
 ```diff  
 +  MPI supported with Flux and 
 + 'correct' versions of MPI 
 ```
   </td>
 <td>  
   
 ```diff 
 + openMP
 ```
   </td>
 <td>  
   
 ```diff   
 + MPI/OpenMP 
 ```
 </td>
 <td> 
  
 ```diff 
 + MPI/OpenMP
 ```
  </td>
</tr>


 <tr> <th> SLURM integration</th>	<td>
      
 ```diff 
 ! Yes but needs to be 
 ! used carefully
 ```
 </td>
     <td>
        
 ```diff      
 ! Yes (partial)
 ```
 </td>
     <td>
        
 ```diff  
 + Yes, either using srun 
 + for job steps or Flux 
 ```
   </td>
 <td>  
   
 ```diff 
 + Yes
 ```
   </td>
 <td>  
   
 ```diff   
 ! honestly the whole system 
 ! works best when executed 
 ! just inside the job, so 
 ! no real integration is 
 ! needed for most applications  
 ```
 </td>
 <td> 
  
 ```diff 
 ! Yes, but you can't easily tailor 
 ! queue parameters for individual 
 ! subtasks (workflow will 
 ! use fixed number of resources)
 ```
  </td>
</tr>



 <tr> <th> SWhat kind of jobs/workload this is good for?</th>	<td>
      
 ```diff 
 + Complex workflows with 
 + several dependencies
 ```
 </td>
     <td>
        
 ```diff      

 ```
 </td>
     <td>
        
 ```diff  
 + More complicated workflows 
 + with several steps  
 ```
   </td>
 <td>  
   
 ```diff 
 
 ```
   </td>
 <td>  
   
 ```diff   
 + Large numbers of short jobs 
 + that are mostly independent
 + of each other
 ```
 </td>
 <td> 
  
 ```diff 
 + Complicated workflows 
 + with several (dependent)
 + steps. 
 #  Not for farming
 # (jobsteps are created)
 ```
  </td>
</tr>
</table>

