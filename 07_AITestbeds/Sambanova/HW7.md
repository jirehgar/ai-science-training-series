## Homework Solution
For the BERT example I changed the number of tasks in this case represented by the --ntasks flag. In the default script these were initialized to use 16 tasks (16 x 8 cores total) and in the other test I changed the script to compile the model with 8 tasks (8 x 8 cores total). Often times, the efficiency or level or parallelization that a model will benefit from depends on some sort of metric that is innate in the model. For this test, I expected that increasing the number of tasks would improve the efficiency of the model.

The only metric I could find from the bert output was the amortized resources overall. These are the resources used for --ntasks 16. As follows is a snapshot from the log file `/home/jireh/ai-science-training-series/07_AITestbeds/Sambanova/bert/112624.18/BertLarge.out`

![image](https://github.com/user-attachments/assets/96a4b953-d37f-4faf-a8d8-3d42eb31464b)

These are the resources used for --ntasks 8. As follows is a snapshot from the log file contained in `/home/jireh/ai-science-training-series/07_AITestbeds/Sambanova/bert/112624.20/BertLarge.out`.

![image](https://github.com/user-attachments/assets/edd4d3d0-8c70-4d99-9e47-5b83dc86acd9)

Even though I decreased the number of tasks, the FLOPS are exactly the same when we change from 16 to 8 tasks. For some reason in this particular implementation of bert-large, the efficiency does not change from 16 to 8 tasks. 
