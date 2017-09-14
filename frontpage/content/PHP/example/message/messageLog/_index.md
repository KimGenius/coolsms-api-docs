+++
title="메시지내역 보기"
weight=8
+++
#### &ndash; 발송 한 메시지 내역을 확인 할 수 있습니다.<br/>
#### &ndash; 관련 Parameter 들은 [Reference gruide](https://www.coolsms.co.kr/opage/manual/php/index.html)를 참고 해주세요.
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

    // set necessary options
    $options = new stdClass();
    $options->message_id = 'M52CB443257C61'; // message id
    // $options->group_id = 'G52CB4432576C8'; // group id
    // $options->count = '40'; //result return counts. default is 20
    /** 자세한 Parameter는 Reference guide를 참고해주세요. **/

    $result = $rest->sent($options);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
