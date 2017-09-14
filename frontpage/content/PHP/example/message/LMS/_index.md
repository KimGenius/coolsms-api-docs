+++
title = "LMS(장문) 발송"
weight = 2
+++

#### &ndash; 2000바이트( 한글 1000자 ) 이내의 내용을 문자 메시지로 보낼 수 있습니다.
#### &ndash; $options->type 을 'LMS'로 바꿔주시면 됩니다.

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
    $options->type = 'LMS';
    $options->text = 'LMS는 2000byte, 한글로 1000자까지 가능합니다!';

    $result = $rest->send($options);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
