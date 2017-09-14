+++
title="메시지 넣기(Json 형식)"
weight=6
+++

#### &ndash; JSON 형식으로 된 메시지 리스트를 받아서 해당 그룹안에 메시지를 넣을 수 있습니다.
#### &ndash; 아래 예제와 같이 텍스트값 등 다양하게 정렬된 메시지를 서버에 JSON 형식으로 보내줍니다.
#### &ndash; 그룹안에 메시지를 넣을 뿐, 실제로 메시지를 발송 하는 건 아닙니다.
#### &ndash; $messages에 원하는 만큼 Object를 넣을 수 있습니다.
#### &ndash; (알림톡 사용시) Sender Key와 Template Code는 필수입니다. 옆에 링크 페이지에 가셔서 발급받아주세요. 발급받기
#### &ndash; (알림톡 사용시) $message->type을 ATA로 해주세요.
#### &ndash; (알림톡 사용시) $message->sender_key, $options->template_code에 발급받으신 Sender Key와 Template Code를 넣어주세요.
#### &ndash; (알림톡 사용시) $message->text에는 해당 Template Code와 같은 형태의 내용만 입력 가능하며 {홍길동}과 같이 {}로 둘러 쌓여있는 부분은 다른 내용으로 변환이 가능합니다.

```php
<?php
/**
 * #example_add_messages
 *
 * This sample code demonstrate how to add json type messages into group through CoolSMS Rest API PHP
 * for more info, visit
 * www.coolsms.co.kr
 */

use Nurigo\Api\GroupMessage;
use Nurigo\Exceptions\CoolsmsException;

require_once __DIR__ . "/../../bootstrap.php";

// api_key and api_secret can be obtained from www.coolsms.co.kr/credentials
$api_key = '#ENTER_YOUR_OWN#';
$api_secret = '#ENTER_YOUR_OWN#';

try {
    // initiate rest api sdk object
    $rest = new GroupMessage($api_key, $api_secret);

    // options(message, group_id) are mandatory. must be filled
    $options = new stdClass();

    $text = array(
        0 => "안녕하세요.",
        1 => "10000건을 20초안에 발송하는 빠르고 저렴한",
        2 => "CoolSMS의 테스팅 문자입니다.");

    $messages = array();
    foreach($text as $val) {
      $message = new stdClass();
      $message->type = "SMS";
      $message->to = "01000000000";
      $message->from = "01000000000";
      $message->text = $val;
      $messages[] = $message;

      // Optional parameters for your own needs
      // $message->type = 'SMS';                       // Message type ( SMS, LMS, MMS, ATA )
      // $message->image_id = 'IM289E9CISNWIC'         // image_id. type must be set as 'MMS'
      // $message->refname = '';                       // Reference name 
      // $message->country = 82;                       // Korea(82) Japan(81) America(1) China(86) Default is Korea
      // $message->datetime = '20140106153000';        // Format must be(YYYYMMDDHHMISS) 2014 01 06 15 30 00 (2014 Jan 06th 3pm 30 00)
      // $message->subject = 'Hello World';            // set msg title for LMS and MMS
      // $message->delay = 10;                         // '0~20' delay messages
      // $message->sender_key = '55540253a3e61072...'; // 알림톡 사용을 위해 필요합니다. 신청방법 : http://www.coolsms.co.kr/AboutAlimTalk
      // $message->template_code = 'C004';             // 알림톡 template code 입니다. 자세한 설명은 http://www.coolsms.co.kr/AboutAlimTalk을 참조해주세요.
    }
    $options->messages = $messages;
    $options->group_id = 'GID57317013931B0';  // group id
    $result = $rest->addMessagesJSON($options);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getCode(); // get error code
}
```
