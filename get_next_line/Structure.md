## Structure of get_next_line

---

get_next_line의 구조는 크게 5가지로 나뉘어진다.

- Initialize Variable
- Parsing data of file
- Find the new line
- Move data
- Return

### Initialize Variable

- 초기 메모리 할당
  - 함수에서 사용되는 2개의 포인터 변수에 대한 메모리 할당
    - buffer : 파일에서 읽은 데이터를 저장하는 변수.
    - line : get_next_line의 파라미터로 들어오는 변수로 new line 까지의 값을 담는다.
- 초기값 선언
  - 위에서 메모리를 할당한 변수들에 널값 대입.
- 에러사항들에 대한 early return
  1. fd 값이 음수인 경우.
  2. BUFFER SIZE가 1보다 작은 경우
  3. get_next_line에 들어오는 파라미터인 line의 주소값이 NULL인 경우
  4. 메모리 할당에 실패하는 경우

### Parsing data of file

- Read the file

  - 파일을 읽고 그 값을 buffer에 저장한다.

    get_next_line에서는 buffer의 값을 static 변수에 담아놓고 사용한다.

    이후의 코드에서 static 변수 내 값에 new line이 있는 경우엔 new line까지 값을 가져오고 뒤에 남은 값은 남겨놓는다.

    다음 new line을 찾을 때, 이전 new line 뒤부터 데이터를 가져와야 함으로 static 변수에 값이 남아있는 경우에는 파일을 읽어오지 않는다.

  - CODE

    ```c
    if (copy[fd][0] == '\0')	// static 변수에 값이 없을 때 동작
    {
    	if ((numread = read(fd, buffer, BUFFER_SIZE)) == 0)	// read 값이 0일 때 동작
    	{
    		free (buffer);
    		return (0);	// 0 반환 (EOF)
    	}
        if (numread < 0)	// numread가 음수일 때 동작
            return (-1);	// -1 반환 (Error)
        ft_strlcpy(copy[fd], buffer, numread + 1);	//buffer 값을 static 변수 copy로 복사
    }
    ```

### Find the new line

- 파일에서 읽어온 데이터 중 new line 탐색 및 위치 반환

  - CODE

    ```c
    int	rtn = 0;
    while (*(copy[fd] + rtn))
    {
        if (*copy[fd] + rtn) == '\n')
            return (rtn);
        rtn++;
    }
    return (-1);
    ```

### Move data

- new line 까지의 데이터 저장

  - CODE

    ```c
    if (check_new_line(copy[fd]))	// new line 있는 경우
        ft_strlcpy(temp, copy[fd], new_line_pointer + 1);	// new line 까지 복사
    else	// new line 없는 경우
        ft_strlcpy(temp, copy[fd], BUFFER_SIZE + 1);	// read한 데이터 전체 복사
    *line = strjoin(*line, temp);	// 기존 line에 새로 개행 검사한 데이터를 strjoin
    empty_line(copy[fd]);	// copy[fd]에 저장된 값 중 복사된 값 왼쪽으로 Shift
    ```

- new line 이후의 데이터 저장

  - line까지 저장 된 값을 왼쪽으로 Shift

  - CODE

    ```c
    if (flag == 1)	// copy 의 값 중 일부만 line에 복사되어진 경우
    {
        memmove(&copy[fd][0], &copy[fd][index + 1], BUFFER_SIZE - index - 1);	// 복사된 값만큼 Shift
        num = BUFFER_SIZE - index - 1;
    }
    else
        num = 0;
    whlie (num < BUFFER_SIZE)	// Shift 된 만큼 반복
        copy[fd][num++] = '\0';	// 널 값 대입
    ```

### Return

- flag에 따라 아래와 같은 값을 반환한다.

  - 1 : 정상 동작
  - 0 : End of File
  - -1 : 에러