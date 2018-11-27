# Answers

## 1.:
- This is when losing or overwriting data happens because off two or more processes try to make the same thing at the same time. This is a Race Condition.

## 2.:
- Because on a multi core machine only the core which interacts with the thing gets sleeped and the others can proceed doing what they want.

- So you have the problem on a single core machine the user process could block other processes.

## 3.:
- The secound process waits until the first leave_region(), after that the secound process can enter the critical region.

- The processes wait for each other: so the first one waits for the secound to leave the critical region and then the secound waits for the first one to leave it.

- So my thinking is that when both processes enter at the exact time that they both get the same loser vaariable and then it fails because the one trys to wake the each other, but both dont even sleep.

- it is very important because it makes clear that not two processes at the same time could enter the critical region at the same time, because the "loser" has to wait for the other to finish.

- int loser //shard variable
Bool interested[3]

void enter_region(int process){
  int otherProcess = 2 - process;

  if(process == 1){
      otherProcess = 2;
    }

  int otherSecoundProcess = 1 - process;

  if (process == 2) {
      otherSecoundProcess = 1;
    }

  interested[process] = true;
  loser = process;

  while(loser == process && (interested[otherProcess] && interested[otherSecoundProcess]));

}
