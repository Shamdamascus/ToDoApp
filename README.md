# ToDoApp

// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.1;
 
contract Bloc{ 
   struct Task{
    string task;
       bool isDone;
   }
   
   mapping (address => Task[]) private Users;
 
  function addTask(string calldata _task) external{
      Users[msg.sender].push(Task({
          task:_task,
          isDone:false
      }));
   }
   
   function getTask(uint _taskIndex) external view returns (Task memory){
       Task storage task = Users[msg.sender][_taskIndex];
       return task;
  
   } 
}
