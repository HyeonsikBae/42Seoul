# get_next_line

42 Seoul Circle 1 의 get_next_line 과제를 진행하며 학습한 내용을 정리한 Repository

---

get_next_line 과제는 파일을 읽어들여 개행까지의 내용을 char형 포인터 변수에 저장하고,

정상적으로 기능이 구현되면 1, 파일의 내용이 끝나면 0, 정상적이지 못한 동작엔 -1을 반환하는 프로그램을 작성하는 것이다.

추가로 여러 파일을 번갈아가며 프로그램을 실행시켜도 각 파일에 대해 기능이 정상적으로 동작되어야 한다.

- 선행학습
  - [fd (file descriptor)](https://github.com/HyeonsikBae/42Seoul/blob/master/get_next_line/file_descriptor.md)
- [코드 구조](https://github.com/HyeonsikBae/42Seoul/blob/master/get_next_line/Structure.md)
  - Initialize Variable
  - Parsing data of file
  - Find the new line
  - Move data
  - Return