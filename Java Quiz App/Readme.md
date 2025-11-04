# Quiz App Using Java

### Summary

The project is a console-based quiz application developed in Apache NetBeans 15 as part of the COIT20245 Programming course. The goal was to create an interactive program that could load quiz questions from a text file or predefined code and manage user interactions efficiently.

The development followed a five-phase iterative process:

Phase 1: Implemented the core classes (App, Question, Manager) and ensured each question was asked only once using arrays.

Phase 2: Introduced multiple attempts per question and improved user interaction handling.

Phase 3: Added a logging system (Log and Entry classes) to record user performance and summarize results.

Phase 4: Enhanced functionality to save log data into a text file (report.txt).

Phase 5: Implemented file reading capability to load quiz questions and answers from an external file (quiz.txt).

Testing

- Ten test cases were designed to validate each phase, focusing on question handling, multiple attempts, logging, saving to files, and reading questions from external files.
- All test cases passed successfully, confirming the correctness and reliability of the program.

Bugs & Limitations

- No known bugs were found during testing.

Limitations:

- Depends on correct file paths and formatting.

- Limited to console interface (no GUI).

- Only supports basic question types.

- No input validation or quiz customization options.

### Future Enhancements

- Develop a Graphical User Interface (GUI) for better usability.

- Improve error handling and input validation.

- Add result review, timing, and multi-language support features.
