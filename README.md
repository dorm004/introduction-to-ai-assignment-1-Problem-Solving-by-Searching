# introduction-to-ai-assignment-1-Problem-Solving-by-Searching
เป็นส่วนของการค้นหาแบบ Breadth-First Search (BFS) ในกราฟหรือโครงสร้างข้อมูลที่มีลำดับการเชิงลึก (tree or graph) โดยใช้ Stack เพื่อทำการค้นหาแบบ BFS.

เริ่มต้นจากการเข้าสู่ลูป while โดยทำการตรวจสอบว่า Stack (bfsSearchStack) ยังไม่ว่าง ด้วยเงื่อนไข bfsSearchStack.isEmpty() == 0. ในทำนองเดียวกับการตรวจสอบว่า Stack ไม่ว่าง (not bfsSearchStack.isEmpty()).

ภายในลูป while, ทำการดึงคู่ (state, action) จาก Stack โดยใช้ bfsSearchStack.pop(). state แทนสถานะปัจจุบันที่กำลังค้นหา และ action คือลำดับของการกระทำที่ทำให้ได้สถานะนี้.

จากนั้น, ทำการลูปผ่านคู่ (next_state, n_direction) ที่ได้จากการเรียก problem.getSuccessors(state) ซึ่งสามารถแปลงเป็น "successors" หรือ "neighbors" ของสถานะปัจจุบัน. สำหรับแต่ละ successor, ทำการตรวจสอบว่าสถานะ n_state นั้นๆ ยังไม่ได้ถูกเยี่ยมชม (ไม่อยู่ใน visitedList). ถ้าเป็นเช่นนั้น, ทำการตรวจสอบว่า n_state เป็นเป้าหมาย (goal state) หรือไม่ ถ้าใช่ ก็ทำการเพิ่มคู่ (n_state, action + [n_direction]) เข้า Stack และเพิ่ม n_state เข้า visitedList. ถ้า n_state ไม่ใช่เป้าหมาย, ก็เพิ่มคู่ (n_state, action + [n_direction]) เข้า Stack เท่านั้น.

โค้ดนี้ดำเนินการไปเรื่อยๆ จนกว่า Stack จะว่าง หรือเจอเป้าหมาย และถ้าเจอเป้าหมายก็จะคืนลำดับของการกระทำที่ทำให้ไปยังเป้าหมายนั้น
