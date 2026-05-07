# Assignment 3 - Complete Documentation

**Student Name**: [Razan alharbi]  
**Student ID**: [445052130]  
**Date Submitted**: [7/5/2026]

---

## 🎥 VIDEO DEMONSTRATION LINK (REQUIRED)

> **⚠️ IMPORTANT: This section is REQUIRED for grading!**
> 
> Upload your 3-5 minute video to your **PERSONAL Gmail Google Drive** (NOT university email).
> Set sharing to "Anyone with the link can view".
> Test the link in incognito/private mode before submitting.

**Video Link**: [Paste your personal Gmail Google Drive link here]

**Video filename**: `[YourStudentID]_Assignment3_Synchronization.mp4`

**Verification**:
- [ ] Link is accessible (tested in incognito mode)
- [ ] Video is 3-5 minutes long
- [ ] Video shows code walkthrough and commits
- [ ] Video has clear audio
- [ ] Uploaded to PERSONAL Gmail (not @std.psau.edu.sa)

---

## Part 1: Development Log (1 mark)

Document your development process with **minimum 3 entries** showing progression:

### Entry 1 - [7may, 6:40pm]
**What I implemented**: 
first commit add my ID
**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 
3min
---

### Entry 2 - [7may, 7:20pm]
**What I implemented**: 
 finish edit code ( todo1 and todo2 )
**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 
maybe 20min
---

### Entry 3 - [7may, 2:27]
**What I implemented**: 
finsh edit code ( todo3)
**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 
8min
---

### Entry 4 - [7may, 7:50]
**What I implemented**: 
finsh edit code (todo4)
**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 
20min
---

### Entry 5 - [Date, Time]
**What I implemented**: 

**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 

---

## Part 2: Technical Questions (1 mark)

### Question 1: Race Conditions
**Q**: Identify and explain TWO race conditions in the original code. For each:
- What shared resource is affected?
- Why is concurrent access a problem?
- What incorrect behavior could occur?

**Your Answer**:
[A race condition occurs when multiple threads try to update contextSwitchCount or totalWaitingTime simultaneously, causing some updates to be lost. This happens because operations like count++ are not atomic and can be interrupted
]

---

### Question 2: Locks vs Semaphores
**Q**: Explain the difference between ReentrantLock and Semaphore. Where did you use each in your code and why?

**Your Answer**:

[I used ReentrantLocks to protect specific data (counters and logs) from concurrent access, and a Semaphore to control access to the CPU resource. Locks ensure data integrity, while Semaphores manage the flow of processes]

---

### Question 3: Deadlock Prevention
**Q**: What is deadlock? Explain TWO prevention techniques and what you did to prevent deadlocks in your code.

**Your Answer**:

[Deadlock is when threads wait for each other forever; I prevented it by using try-finally blocks to ensure locks are always released. I also avoided nested locks by using a fine-grained locking design.]

---

### Question 4: Lock Granularity Design Decision 
**Q**: For Task 1 (protecting the three counters), explain your lock design choice:
- Did you use ONE lock for all three counters (coarse-grained) OR separate locks for each counter (fine-grained)?
- Explain WHY you made this choice
- What are the trade-offs between the two approaches?
- Given that the three counters are independent, which approach provides better concurrency and why?

**Your Answer**:

[I chose Fine-grained locking (separate locks) because the counters are independent. This approach provides better concurrency and performance as threads don't have to wait for a single global lock to update unrelated data.]

---

## Part 3: Synchronization Analysis (1 mark)

### Critical Section #1: Counter Variables

**Which variables**: 
contextSwitchCount, completedProcessCount, and totalWaitingTime.
**Why they need protection**: 

**Synchronization mechanism used**: 
These are shared variables accessed by multiple threads. Without protection, "lost updates" occur because the increment operation (++) is not atomic.
**Code snippet**:
```java
// Paste your implementation here
```

**Justification**: 
Using separate locks for each counter allows threads to update different statistics simultaneously, improving performance while ensuring data accuracy
---

### Critical Section #2: Execution Log

**What resource**: 
The ArrayList<String> executionLog
**Why it needs protection**: 
ArrayList is not thread-safe. If two processes try to add a log message at the same time, it can lead to data corruption or a ConcurrentModificationException
**Synchronization mechanism used**: 
ReentrantLock (specifically logLock).
**Code snippet**:
```java
// Paste your implementation here
```

**Justification**: 
The lock ensures that only one thread can modify the log list at a time, maintaining a consistent and ordered history of execution.
---

### Critical Section #3: CPU Semaphore

**Purpose of semaphore**: 
To simulate the CPU resource and control process execution flow
**Number of permits and why**: 
This makes it a "Binary Semaphore," ensuring that only one process can be "Running" on the CPU at any given moment.
**Where implemented**: 
In the run() method of the Process class
**Code snippet**:
```java
// Paste your implementation here
```

**Effect on program behavior**: 
prevents multiple processes from executing their logic simultaneously, correctly simulating a single-core CPU environment where processes must wait their turn.
---

## Part 4: Testing and Verification (2 marks)

### Test 1: Consistency Check
**What I tested**: Running program multiple times to verify consistent results

**Testing procedure**: 
```bash
# Commands used (run the program at least 5 times)
```

**Results**: 
(Show that running multiple times produces consistent, correct results)

**Why synchronization is necessary**: 
(Explain what race conditions COULD occur without synchronization, even if you didn't observe them. Explain which shared resources need protection and why.)

**Conclusion**: 

---

### Test 2: Exception Testing
**What I tested**: Checking for ConcurrentModificationException

**Testing procedure**: 

**Results**: 

**What this proves**: 

---

### Test 3: Correctness Verification
**What I tested**: Verifying correct final values (total burst time, context switches, etc.)

**Expected values**: 

**Actual values**: 

**Analysis**: 

---

### Test 4: Different Scenarios
**Scenario tested**: [e.g., different time quantum, more processes, etc.]

**Purpose**: 

**Results**: 

**What I learned**: 

---

## Part 5: Reflection and Learning

### What I learned about synchronization:

[I learned that synchronization is essential to prevent Race Conditions when multiple threads access shared data. Using ReentrantLocks ensures mutual exclusion, while the try-finally block prevents Deadlocks by ensuring locks are always released. I also learned that Fine-grained locking (using multiple locks) improves performance by allowing independent resources to be updated simultaneously. Finally, Semaphores helped me control the execution flow and simulate CPU access limits.]

---

### Real-world applications:

Give TWO examples where synchronization is critical:

**Example 1**: 
Banking Systems: To ensure account balances are updated correctly when multiple transactions happen at once.
**Example 2**: 
Ticket Booking: To prevent the same seat from being sold to two different customers simultaneously.
---

### How I would explain synchronization to others:

[Explain to someone who just finished Assignment 1 - use simple terms and analogies]

---

## Part 6: GitHub Repository Information

**Repository URL**: 

**Number of commits**: 

**Commit messages**: 
1. 
2. 
3. 
4. 

---

## Summary

**Total time spent on assignment**: 
2hours
**Key takeaways**: 
1. 
2. 
3. 

**Most challenging aspect**: 

**What I'm most proud of**: 

---

**End of Documentation**
