+++
title="예약문자 발송"
weight=4
+++
#### &ndash; 예약해둔 날짜에 문자 메시지를 보낼 수 있습니다.<br/>
#### &ndash; $options->datetime 에 날짜를 넣어주세요. 예) '20160221150000' // 2016년 2월 21일 15시 00분 00초
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
    $options->type = 'SMS';
    $options->text = '예약해둔 날짜에 문자를 보낼 수 있습니다!';
    $options->datetime = '20140106153000'; // Format must be(YYYYMMDDHHMISS) 2014 01 06 15 30 00 (2014 Jan 06th 3pm 30 00)

    $result = $rest->send($options);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
