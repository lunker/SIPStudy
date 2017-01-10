# INVITE
- ask a server to establish a session.
- UAC는 1개 이상의 2xx response나 non-2xx final response를 받을 수 있다.  
- UAC는 final response를 받을때 마다 ack를 보내야 한다.
-> 300 ~ 699의 final response는 transaction layer에서 ack가 처리된다.
-> 2xx final response는 uac core에 의해서 ack가 발행된다.


#### Creating the Initial Invite(13.2.1)
- Expire Header : 지정된 시간동안에 INVITE에 대한 final response를 받지 못하면 uac가 해당 request를 CANCEL을 보내서 취소시킨다.  
-

#### 2xx response  
- multiple 2xx response를 받을 수 있다.
- 2xx response에 대한 ack는 기존 dialog에서 쓰인 header field와 동일해야 한다.
-

### UAS PROCESSING

#### Processing of the INVITE
-
 
