# sip UAC basic behavior

#### uas behavior(rfc 3261, section 8.2)
- request header에 to tag가 존재해야만 한다.
- to tag가 존재하는 request에 대하여, dialog identifier는 계산하고, 이를 기존에 존재하는 dialog들과 비교하여 매칭되는게 있는지 확인한다.
- if) find matching dialog, 이 request는 mid-dialog request이다. 이때에는 outside of dialog request와 동일하게 처리한다.(section 8.2참고)

- if) to tag는 존재하지만, 일치되는 dialog가 없는 경우,
 uas가 뒤졌거나, misroute된 경우이다.

1) method inspection
- 지원되지 않는 method이면, 405 response를 보낸다.
- 405 reponse와 함께 Header의 ALLOW field에 사용 가능한 Method list를 추가한다.  

2) header inspection
-
---

#### uac behavior(rfc 3261, 8.1)
**uac behavior outside of a dialog**  
- INVITE, OPTION이 해당된다.  
