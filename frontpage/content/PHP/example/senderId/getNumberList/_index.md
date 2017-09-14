+++
title="발신번호 리스트 가져오기"
weight=3
+++

#### &ndash; 발신번호 리스트를 확인합니다.
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
 
    $result = $rest->senderidList(); 
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
