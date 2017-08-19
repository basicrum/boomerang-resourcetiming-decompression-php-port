# boomerang-resourcetiming-decompression-php-port
PHP port of popular JavaScript plugin for compressing Resource Timing data for Boomerang JS library.

# Credits:
 * Author and maintainer of original JavaScript library: Nic Jansma (http://nicj.net)
 * The original JavaScript library can be found here: https://github.com/nicjansma/resourcetiming-compression.js
 * More about the JavaScript library: http://nicj.net/compressing-resourcetiming

# Example usage:

```php

<?php
require_once 'resourcetimingDecompression.0.3.4.php';

$testInput = '{
        "http://": {
            "foo.com/": {
                "js/foo.js": "370,1z,1c|390,1,2",
            "css/foo.css": "48c,5k,14"
        }
    }
}';

$resourceTimingDecompression = new ResourceTimingDecompression_v_0_3_4();

$output = $resourceTimingDecompression->decompressResources(json_decode($testInput, true));
print_r($output);

/**
 * Array
 * (
 *     [0] => Array
 *     (
 *         [name] => http://moc.oof/js/foo.js
 *             [initiatorType] => script
 *             [startTime] => 252
 *             [redirectStart] => 0
 *             [redirectEnd] => 0
 *             [fetchStart] => 252
 *             [domainLookupStart] => 0
 *             [domainLookupEnd] => 0
 *             [connectStart] => 0
 *             [secureConnectionStart] => 0
 *             [connectEnd] => 0
 *             [requestStart] => 0
 *             [responseStart] => 300
 *             [responseEnd] => 323
 *             [duration] => 71
 *         )
 *
 * [1] => Array
 * (
 *     [name] => http://moc.oof/js/foo.js
 *             [initiatorType] => script
 *             [startTime] => 324
 *             [redirectStart] => 0
 *             [redirectEnd] => 0
 *             [fetchStart] => 324
 *             [domainLookupStart] => 0
 *             [domainLookupEnd] => 0
 *             [connectStart] => 0
 *             [secureConnectionStart] => 0
 *             [connectEnd] => 0
 *             [requestStart] => 0
 *             [responseStart] => 326
 *             [responseEnd] => 325
 *             [duration] => 1
 *         )
 *
 * [2] => Array
 * (
 *     [name] => http://moc.oof/css/foo.css
 *             [initiatorType] => css
 *             [startTime] => 300
 *             [redirectStart] => 0
 *             [redirectEnd] => 0
 *             [fetchStart] => 300
 *             [domainLookupStart] => 0
 *             [domainLookupEnd] => 0
 *             [connectStart] => 0
 *             [secureConnectionStart] => 0
 *             [connectEnd] => 0
 *             [requestStart] => 0
 *             [responseStart] => 340
 *             [responseEnd] => 500
 *             [duration] => 200
 *         )
 *
 * )
 */
```
