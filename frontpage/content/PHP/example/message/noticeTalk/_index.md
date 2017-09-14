+++
title="알림톡 발송"
weight=5
+++
&ndash; Sender Key와 Template Code는 필수입니다. 옆에 링크 페이지에 가셔서 발급받아주세요. [발급받기](https://www.coolsms.co.kr/index.php?mid=AboutAlimTalk)<br/>
#### &ndash; $options->type을 ATA로 해주세요.<br/>
#### &ndash; $options->sender_key, $options->template_code에 발급받으신 Sender Key와 Template Code를 넣어주세요.<br/>
#### &ndash; $options->text에는 해당 Template Code와 같은 형태의 내용만 입력 가능하며 {홍길동}과 같이 {}로 둘러 쌓여있는 부분은 다른 내용으로 변환이 가능합니다.

```php
use Nurigo\Api\Message;
use Nurigo\Exceptions\CoolsmsException;

require_once __DIR__ . "/../../vendor/autoload.php";

// api_key and api_secret can be obtained from www.coolsms.co.kr/credentials
$api_key = '#ENTER_YOUR_OWN#';
$api_secret = '#ENTER_YOUR_OWN#';

try {
    // initiate rest api sdk object
    $rest = new Message($api_key, $api_secret);

    // 4 options(to, from, type, text) are mandatory. must be filled
    $options = new stdClass();
    $options->to = '01000000000';
    $options->from = '01000000000';
    $options->type = 'ATA';
    $options->text = '메시지 내용은 template_code의 내용과 같아야 하며 내용중 변수 부분만 다르게 바꿀 수 있습니다.'; // 변수 예) {홍길동} -> 이하이
    $options->sender_key = '55540253a3e61072...'; // 알림톡 사용을 위해 필요합니다. 신청방법 : http://www.coolsms.co.kr/AboutAlimTalk
    $options->template_code = 'C004';             // 알림톡 template code 입니다. 자세한 설명은 http://www.coolsms.co.kr/AboutAlimTalk을 참조해주세요.

    $result = $rest->send($options);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
