# 인터럽트 받을 포트 설정 EIMSK(External Interrupt Mask Register) 
![image](https://user-images.githubusercontent.com/106857769/198840806-8bdae9bb-0fcd-4d03-8ed6-e1f8ce202429.png)
~~~

~~~

# 각 인터럽트 동작모드 설정 EICRA,EICRB
![image](https://user-images.githubusercontent.com/106857769/198840748-a44da35a-adc7-4592-8277-e92c7d599b64.png)
![image](https://user-images.githubusercontent.com/106857769/198840766-63a78471-c8ea-4e9c-855c-a4965e43487e.png)


# CPU 설정부분
![image](https://user-images.githubusercontent.com/106857769/198840838-a976befd-28ea-4aab-ae60-a142abe734b9.png)



# 인터럽트 처리 부분
~~~
  ISR(INT0_vect)
  { 
   // ISP(인터럽트 서비스 루틴) 
   // = 인터럽트 처리 프로그램 
  } 
~~~
