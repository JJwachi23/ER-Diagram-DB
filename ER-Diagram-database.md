``` mermaid
graph TD
    Start(["เริ่มต้นโครงการ"]) --> Requirements["1. เก็บความต้องการของระบบ<br/>(รู้ว่าต้องเก็บข้อมูลอะไรบ้าง ใช้งานยังไง)"]

    subgraph Phase1 ["Phase 1: ออกแบบ ER-Diagram (วาดพิมพ์เขียว)"]
        Requirements --> ConceptualERD["2. สร้าง Conceptual ERD<br/>(วาดแค่กล่อง Entity และเส้นความสัมพันธ์คร่าวๆ)"]
        ConceptualERD --> LogicalERD["3. สร้าง Logical ERD (เหมือนภาพที่ส่งมา)<br/>- ใส่ Attributes (ชื่อคอลัมน์)<br/>- กำหนด PK/FK"]
        LogicalERD --> Review{"4. ตรวจสอบความถูกต้อง<br/>(ครบไหม? ถูกไหม?)"}
        Review -- "ยังไม่ดีพอ (แก้ไข)" --> LogicalERD
    end

    Review -- "ผ่าน! (พิมพ์เขียวเสร็จแล้ว)" --> PhysicalDesign

    subgraph Phase2 ["Phase 2: สร้าง Database Schema (ลงมือสร้าง)"]
        PhysicalDesign["5. กำหนด Physical Design<br/>- เลือกชนิดข้อมูล (int, varchar)<br/>- เลือก Storage Engine"]
        PhysicalDesign --> GenerateSchema["6. สร้าง Database Schema จริง<br/>(เขียนโค้ด SQL: CREATE TABLE...)"]
    end

    GenerateSchema --> Implementation["7. นำไปใช้งาน/Deploy ลง Server"]
    Implementation --> End(["สิ้นสุด"])

    %% ตกแต่งสีสัน
    classDef planning fill:#f9f,stroke:#333,stroke-width:2px,color:black;
    classDef building fill:#ccf,stroke:#333,stroke-width:2px,color:black;
    class LogicalERD,ConceptualERD,Review planning;
    class PhysicalDesign,GenerateSchema building;
    style Start fill:#ffcccb,stroke:#f66,stroke-width:2px,color:black
    style End fill:#90ee90,stroke:#333,stroke-width:2px,color:black
```