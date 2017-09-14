+++
title="그룹 삭제"
weight=3
+++

#### &ndash; 해당 그룹을 삭제 합니다.
#### &ndash; 주의! 그룹안의 메시지들이 전부 삭제 됩니다.

```php
use Nurigo\Api\GroupMessage;
use Nurigo\Exceptions\CoolsmsException;
 
require_once __DIR__ . "/../../vendor/autoload.php";
 
// api_key and api_secret can be obtained from www.coolsms.co.kr/credentials
$api_key = '#ENTER_YOUR_OWN#';
$api_secret = '#ENTER_YOUR_OWN#';
 
try {
    // initiate rest api sdk object
    $rest = new GroupMessage($api_key, $api_secret);
 
    // group_ids are mandatory. must be filled
    $group_ids = 'GID56CC00E21C4DC'; // ex) '1GCOLS23BDG','RGGBB11545'
 
    $result = $rest->deleteGroups($group_ids);
    print_r($result);
} catch(CoolsmsException $e) {
    echo $e->getMessage(); // get error message
    echo $e->getCode(); // get error code
}
```
