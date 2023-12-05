# Evaluation Code


## Introduction
In this folder, we provide the evaluation notebooks. Please note that the numbers present in the cells within each notebook will be what we report in our leaderboard. These cells have been preexecuted to archive the accuracy scores.

These notebooks serve as an archival of our evaluation procedure, and as a way of showing the way we benchmark OpenAI's models.

## Common Questions

1. **How do I benchmark Raven?**
   Please [spin up a TGI endpoint](https://huggingface.co/docs/inference-endpoints/guides/create_endpoint) using our [RavenV2 weights](https://huggingface.co/Nexusflow/NexusRaven-V2-13B). Then, please replace the existing URL with yours in the notebook and run the cells. 

3. **Should I expect consistency for Raven's results?**
   Yes. NexusRaven-V2 is benchamrked with sampling turned off, and therefore, the accuracy should be identical each run.

4. **GPT4's scores vary a lot!**
   Yes, this is expected. GPT4 is a sparse MoE, and due to the way batching is done via the API Endpoint, sequence-level determinism cannot be guranteed by OpenAI due to non-deterministic expert routing (due to batching). Therefore, the scores for GPT4 can swing wildly across runs for any given task. However, the average across tasks should be more constant and less variant.

6. **Why aren't you using the Function Calling API directly?**
   Function calling API does not support nested functions (i.e. ```f(x(b(), c()))```, etc.), and in order to keep evaluation consistent across tasks, we opted for the current method. However, it is worthwhile to note that we benchmarked a few of the single API tasks via the function calling API, and we observed no higher numbers; in some cases, the numbers were noticably lower than direct python-style function calling.



