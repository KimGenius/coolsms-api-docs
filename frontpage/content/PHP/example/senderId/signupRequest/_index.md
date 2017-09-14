+++
title="등록 요청"
weight=1
+++

#### &ndash; 발신번호 등록을 요청합니다.
#### &ndash; 1544-****와 같은 번호나 등록이 되지 않는 전화번호는 증빙자료를 이용한 발신번호 등록을 이용해주세요. => [바로가기](http://www.coolsms.co.kr/index.php?mid=service_setup&act=dispSmsconfigSenderNumbers)

```php
use Nurigo\Api\SenderID;
use Nurigo\Exceptions\CoolsmsException;
 
require_once __DIR__ . "/../../vendor/autoload.php";
 
// api_key and api_secret can be obtained from www.coolsms.co.kr/credentials
$api_key = '#ENTER_YOUR_OWN#';
$api_secret = '#ENTER_YOUR_OWN#';
 
try {
    // initiate rest api sdk object
    $rest = new SenderID($api_key, $api_secret);
 
    // phone are mandatory. must be filled
    $phone = '01000000000'; // sender number to register 
 
    $result = $rest->register($phone); // 
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```

