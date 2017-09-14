+++
title="MMS(포토문자) 발송"
weight=3
+++

#### &ndash; 이미지( 300KB미만의 2024x2024이하 JPG, GIF, PNG ) 를 포함한 내용을 문자 메시지로 보낼 수 있습니다.<br/>
#### &ndash; $options->type 을 'MMS'로 바꿔주세요.<br/>
#### &ndash; $options->image 에 해당 경로와 함께 이미지 파일명을 넣어주세요. 예) './images/test.jpg'

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
    $options->type = 'MMS';
    $options->text = 'MMS는 이미지가 포함된 문자입니다~!';
    $options->image = 'desert.jpg';

    $result = $rest->send($options);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
