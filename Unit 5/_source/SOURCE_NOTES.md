# Unit 5 (Input/Output Organizations) — Source Map
Prepared for CSE23CT201 Unit 5. Records exactly which textbook chapters map to
which Unit-5 topic, so a future rebuild need not rediscover the split.

## Key finding
This edition of Hamacher ("Computer Organization and Embedded Systems") is the
REORGANISED one. The Unit-5 syllabus content is split across THREE chapters — it
is NOT all in Ch.7:
- **Ch.3 "Basic Input/Output"**  → Accessing I/O Devices, Interrupts (hardware,
  enable/disable, multiple devices, vectored/daisy-chain, priority), Exceptions,
  use of interrupts in the OS.
- **Ch.8 "The Memory System" §8.4** → Direct Memory Access (Fig 8.12 DMA registers,
  Fig 8.13 DMA in a system). (Deliberately excluded from Unit 4, reserved for here.)
- **Ch.7 "Input/Output Organization"** → §7.2 Synchronous/Asynchronous buses
  (Figs 7.3, 7.5, 7.6, 7.7), §7.3 Arbitration (Figs 7.8, 7.9), §7.5 Interconnection
  Standards → PCI (Fig 7.18, 7.19, Table 7.1) and SCSI.

## Notes chapters (match the config's M5 module 1:1)
1. Accessing I/O Devices        — Ch.3 §3.1  (Fig 3.1, 3.2, 3.3)
2. Interrupts                   — Ch.3 §3.2  (Fig 3.6, 3.7)
3. Exceptions & Interrupts/OS   — Ch.3 §3.2.6 + OS use
4. DMA & Bus Arbitration        — Ch.8 §8.4 (Fig 8.12, 8.13) + Ch.7 §7.3 (Fig 7.8, 7.9)
5. Synchronous vs Async Buses   — Ch.7 §7.2 (Fig 7.3, 7.5, 7.6, 7.7)
6. Standard I/O: PCI & SCSI     — Ch.7 §7.5 (Fig 7.18, 7.19, Table 7.1)

## Source textbook PDFs (on device)
C:\Users\Aishwarya\OneDrive\SRET 2026-27\COA\text book split & ppts and well explained ppts\
  Hamacher_Ch03_Basic_Input_Output.pdf
  Hamacher_Ch07_Input_Output_Organization.pdf
  Hamacher_Ch08_The_Memory_System.pdf
Professor's reference deck: ...\ppts\Unit5_Input_Output_Organizations.pptx/.pdf

## Deliverables produced
- Notes: Unit5_InputOutputOrganizations_Notes.html  (COA_Classroom\Unit 5\)
- Foothold lessons: Unit5_1..Unit5_6 + Unit5_C  (course_COA\src\lessons\)
