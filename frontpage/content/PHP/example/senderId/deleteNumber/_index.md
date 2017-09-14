+++
title="발신번호 삭제"
weight=4
+++

#### &ndash; 해당 handle_key를 가지고 있는 발신번호를 삭제합니다.

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
    $handle_key = 'C29CE02IOE9'; // sender number handle key. check for 'example_list'
 
    $result = $rest->delete($handle_key);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getResponseCode(); // get 'api.coolsms.co.kr' response code
}
```
