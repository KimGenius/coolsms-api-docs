+++
title="등록 확인"
weight=2
+++

#### &ndash; 등록 요청한 전화번호로 등록을 확인합니다.
#### &ndash; 등록 요청한 전화번호로 '등록 요청'시 나왔던 ARS 번호에 전화를 걸어주세요.
#### &ndash; '지금은 전화를 받지 않습니다' 등의 메시지가 나오면 정상입니다.
#### &ndash; 프로그램이 확인 할 수 있도록 메시지가 나온 뒤 바로 끊지 말고 잠시 대기 해주세요.
#### &ndash; 위 순서를 거친 후 '등록 요청'에서 받은 Handle_key를 이용해 '등록 확인'을 하시면 됩니다. ( response가 없으면 성공 )

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
 
    // handle_key are mandatory. must be filled
    $handle_key = 'C29CE02IOE9'; // after register call. return value
 
    $result = $rest->verify($handle_key);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
