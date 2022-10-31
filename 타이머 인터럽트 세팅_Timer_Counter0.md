# (TCCR0)
  - Total
    ![image](https://user-images.githubusercontent.com/106857769/198841027-b7f84efc-7e1a-4711-8551-0f72b57612b5.png)
  
  - WGM01:0
    ![image](https://user-images.githubusercontent.com/106857769/198841071-64327d9a-fcb7-4d67-a65a-958ca2e3eec6.png)
    ![image](https://user-images.githubusercontent.com/106857769/198841124-52b0d128-9b61-4972-906b-bff04131c3f6.png)
    - 오버플로우일지 ctc일지 지정
  
  - COM01:0
    ![image](https://user-images.githubusercontent.com/106857769/198841299-ac8fd375-7e29-4bc5-b39e-463d4ad26dab.png)
    ![image](https://user-images.githubusercontent.com/106857769/198841316-3c6bb682-f3d1-4e2e-b608-c96f47eea138.png)
    ![image](https://user-images.githubusercontent.com/106857769/198841339-8dd974fe-74fe-40fe-98a0-727caeb57cf4.png)
    - 아마도 이게 CTC 일때 특정핀에 펄스 출력하는거 였던거같음
    
      ~~~
      ____----____----____----____----____----____----____----____----____

      ----____----____----____----____----____----____----____----____----

      ----^----^----^----^----^----^----^----^----^----^----^----^----

      ----v----v----v----v----v----v----v----v----v----v----v----v----
      ~~~
    
    이 중 어떤식으로 펄스 출력할건지 지정..?
    
  - CS02:0
    - 분주 쪼개기
      ![image](https://user-images.githubusercontent.com/106857769/198841431-afaefc54-0d68-4e65-baf6-88b9c0f5bb9b.png)


# Timer/Counter (TCNT0)
  - Total
    ![image](https://user-images.githubusercontent.com/106857769/198841547-764cb50f-a112-4611-b013-80651ba145d7.png)
    
    - TCNT0=256-x
      분주 한번더



# Output Compare Register (OCR0)
  - Total
    ![image](https://user-images.githubusercontent.com/106857769/198841563-627688fa-b150-4d4b-9df9-79013c333901.png)
    - CTC 일때 설정
    
      TCNT 와 반대느낌?
      
      TCNT0=256-x => OCR0=x


#  Timer Interrupt Flag Register (TIFR)
  - Total
    ![image](https://user-images.githubusercontent.com/106857769/198841611-ce9e49f4-9bbc-4925-95f4-93ebcd8e4aa9.png)


# Timer Interrupt Mask Register (TIMSK)
  - Total
    ![image](https://user-images.githubusercontent.com/106857769/198841597-6619fa70-e88b-4f54-b374-fc6467cdb8b1.png)
    
     - 모드 설정 (overflow / ctc)
     
       TIMSK=0x01;//0000 0001 timer0/overflow	
       
       TIMSK= 0x00;//0000 0000 timer0/CTC 이거 맞는건지 모르겠넹..
       
       Timer2 모드 설정하려면 TOV1 설정해주면 됨 설정은 위 0 과 같음
       



