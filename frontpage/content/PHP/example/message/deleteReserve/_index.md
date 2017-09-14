+++
title="예약문자 취소"
weight=6
+++
#### &ndash; 아직 발송되지 않은 예약문자를 취소 할 수 있습니다.<br/>
#### &ndash; $options->mid or gid 안에 해당 문자의 mid나 gid를 넣어주시면 됩니다.
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

    // Either mid or gid must be entered.
    $options = new stdClass();
    $options->mid = 'M52CB443257C61'; // 예약취소 할 message id.
    // $options->gid = 'G52CB4432576C8'; // 예약취소 할 group id.

    $rest->cancel($options); // cancel does not return any.
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
