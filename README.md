# Inventory management system using a 3D Gantry robot.
There is a shelf with 42 spaces. Loading and unloading is done by a 3D gantry robot. The stored parts on the shelf have just an ID which is a 23-character long string.  
The shelf has 7 columns and 6 rows, and no sensors and actuators.  
  
This project provides the following functionalities to manage the shelf spaces:  
- An interface for the robot to get the next free or next occupied shelf space.
- A mechanism for the robot to store/place a part at the next free shelf space.
- A mechanism for the robot to remove/unload parts from the next occupied shelf space.
- Implementation of industry-standard queuing operations based on the FIFO (First-In, First-Out) principle and functionalities for automatically managing inventory.
- An interface for the robot to get the inventory space by part ID. And removing parts exclusively using Part ID.
- Semi-automatic operation of the system, where an operator can Store or remove objects by using manual instructions [Part ID, shelf number for loading and unloading, etc.]
- Error Handling


  
I have been using the PLC IEC-61131-3 language such as,  
- ST - Structured Text (S7-SCL)
- FBD - Function Block Diagram
- LD - Ladder Diagram

Complete control logic is developed in the TIA portal V18.  
CPU : Siemens 1511C -1 PN  
HMI : KTP 700 basic PN (7” Display)  
Industrial Queuing operation (First In - First Out)

Control Code:  
- Main [OB]
  
  ![Screenshot (42)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/51e6f95b-7700-4168-af98-66395d623a69)

      
  ![Screenshot (43)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/8d0b81dc-ac1f-4d8c-8a4b-e398951323de)
  
  ![Screenshot (44)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/c765a986-7c0d-47a3-90b4-dba773b1be49)

  ![Screenshot (45)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/922542f1-3ecd-469d-9aa5-81a87d23b9ff)

- Check available position [FC]

  ![Screenshot (46)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/edcb473a-fd33-4020-9ce8-b466e618d16a)

- Manual Operation [FB]
    
  ![Screenshot (47)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/e3d63e2c-1afe-4817-9023-c96ac044364f)

- Store Function [FC]

    ![Screenshot (48)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/75ae01f7-7c7a-4f4e-95f7-86e764ec9b45)
- Retrive Function [FC]

    ![Screenshot (49)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/7a48b0b8-49f6-4f88-91f3-9cc25bbb6929)
  
- Search by Part ID [FB]

    ![Screenshot (50)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/1cd4368c-7830-4915-a8f7-724ba0b86627)

- LGF FIFO [FB]  
    Utilized Library of General Functions by Siemens for First In - First Out operation
    1. enqueue: Enqueue item to the buffer
    2. dequeue: Dequeue item from the buffer and return it on `item`
    3. elementCount: Number of elements in the buffer
    4. item: The entry that is either returned from the ring buffer or written into the buffer
    5. buffer: The ARRAY that is used as the ring buffer. (Array of…)

   ![Screenshot (51)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/26663e7c-02da-4587-ba02-5c7cdd04bdd6)

- Part ID generation [FB]

  ![Screenshot (52)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/592e9e2f-dd6e-4615-8f51-c3cb06f9bc10)
  
  - CONCAT operation : Combining two strings

  ![Screenshot (53)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/564604a8-bee8-4e67-a52f-2918ca03ab60)

- Part ID in Array [FC]  
   Retaining or discarding the Part ID after subsequently storing or removing parts.

  ![Screenshot (54)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/f1e1f0f3-fdb1-4079-b4a7-f6d1b530a46f)

  ![Screenshot (55)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/450c3460-94ff-4948-ba6d-8bf97d15ee56)

Human Machine Interface [HMI]

- Root Screen
  ![Screenshot (56)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/1c7a29a0-0960-4e46-b737-1687f7c458a0)

- Main Operation Screen
  ![Screenshot (57)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/6a8892fe-e20c-4517-bce7-f35a9f8e93e6)

- FIFO Screen
  ![Screenshot (58)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/5a320aa1-9b2f-4b4a-a2f1-8fdc085330b4)

- Inventory management Visualization
  ![Screenshot (59)](https://github.com/riitesh07/Inventory-Management-System-for-a-3D-Gantry-Robot/assets/68095076/4a9903f1-4192-4afb-a10c-45a7cd59c151)









