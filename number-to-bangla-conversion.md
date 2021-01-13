# প্যাকেজঃ Number to Bangla Conversion

## Number to Bangla Number, Word or Month Name in Laravel

[![Packagist](https://camo.githubusercontent.com/ffba191f1d6ada984cca0bb88844d7b980e4d2e01b34389dc16a299f38a7e474/68747470733a2f2f696d672e736869656c64732e696f2f7061636b61676973742f64742f72616b6962687374752f6e756d6265722d746f2d62616e676c61)](https://camo.githubusercontent.com/ffba191f1d6ada984cca0bb88844d7b980e4d2e01b34389dc16a299f38a7e474/68747470733a2f2f696d672e736869656c64732e696f2f7061636b61676973742f64742f72616b6962687374752f6e756d6265722d746f2d62616e676c61) [![GitHub stars](https://camo.githubusercontent.com/3c3edf684b85b7428285777c107c0d4d745606436325a8983e82275e8fc55bce/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f73746172732f72616b6962756c2d6465762f6e756d6265722d746f2d62616e676c61)](https://github.com/rakibhstu/number-to-bangla/stargazers) [![GitHub forks](https://camo.githubusercontent.com/07d040dcf0800ec61c132b63b37fa15db58a05719b558879de42032f6207ea6c/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f666f726b732f72616b6962756c2d6465762f6e756d6265722d746f2d62616e676c61)](https://github.com/rakibhstu/number-to-bangla/network) [![GitHub issues](https://camo.githubusercontent.com/3140f83d02725aa7851068327a86402a6edaaab768fee1e630400ac37a028046/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6973737565732f72616b6962756c2d6465762f6e756d6265722d746f2d62616e676c61)](https://github.com/rakibhstu/number-to-bangla/issues) [![GitHub license](https://camo.githubusercontent.com/badcc7914deaf054277f65ec6a3b759ce2a7ea1d905f69f428fe6b93d5307ce4/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f72616b6962756c2d6465762f6e756d6265722d746f2d62616e676c61)](https://github.com/rakibhstu/number-to-bangla/blob/master/LICENSE) [![Twitter](https://camo.githubusercontent.com/c03cfc258a17d7e48238102f365ca90b6358b9d195736b0c3b0b36a06e130cac/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f75726c3f7374796c653d736f6369616c2675726c3d68747470732533412532462532467061636b61676973742e6f72672532467061636b6167657325324672616b6962687374752532466e756d6265722d746f2d62616e676c61)](https://twitter.com/intent/tweet?text=Wow:&url=https%3A%2F%2Fpackagist.org%2Fpackages%2Frakibhstu%2Fnumber-to-bangla)

Laravel package to convert English numbers to Bangla number or Bangla text, Bangla month name and Bangla Money Format for Laravel 5.5+. Maximum possible number to covert in Bangla word is 999999999999999 Example,

| Operation | English Input | Bangla Output |
| :--- | :--- | :--- |
| Text \(Integer\) | 13459 | তেরো হাজার চার শত ঊনষাট |
| Text \(Float\) | 1345.05 | এক হাজার তিন শত পঁয়তাল্লিশ দশমিক শূন্য পাঁচ |
| Number | 1345.5 | ১৩৪৫.৫ |
| Text Money Format | 1345.50 | এক হাজার তিন শত পঁয়তাল্লিশ টাকা পঞ্চাশ পয়সা |
| Month | 12 | ডিসেম্বর |
| Comma \(Lakh\) | 121212121 | ১২,১২,১২,১২১ |

## Installation

Install the package through [Composer](http://getcomposer.org/). On the command line:

```text
composer require rakibhstu/number-to-bangla '1.0'

```

## Configuration

If Laravel &gt; 7, no need to add provider

Add the following to your `providers` array in `config/app.php`:

```text
'providers' => [
    // ...

    Rakibhstu\Banglanumber\NumberToBanglaServiceProvider::class,
],
```

## Usage

Here you can see some example of just how simple this package is to use.

```text
use Rakibhstu\Banglanumber\NumberToBangla;

$numto = new NumberToBangla();

// If you want to convert any number (Integer of Float) into Bangla Word
$text = $numto->bnWord(13459);    // Output:  তেরো হাজার চার শত ঊনষাট
$text = $numto->bnWord(1345.05);  // Output:  এক হাজার তিন শত পঁয়তাল্লিশ দশমিক শূন্য পাঁচ
```

### Number to Bangla Word

Use `bnWord()` to convert any number into bangla word. Example,

```text
// Integer
$text = $numto->bnWord(13459);    // Output:  তেরো হাজার চার শত ঊনষাট

// Float
$text = $numto->bnWord(1345.05);    // Output: এক হাজার তিন শত পঁয়তাল্লিশ দশমিক শূন্য পাঁচ
$text = $numto->bnWord(345675.105); // Output: তিন লক্ষ পঁয়তাল্লিশ হাজার ছয় শত পঁচাত্তর দশমিক এক শূন্য পাঁচ
```

### Number to Bangla Money Format

Use `bnMoney()` to convert any number into bangla money format with 'টাকা' & 'পয়সা'. Example,

```text
$text = $numto->bnMoney(13459);     // Output:  তেরো হাজার চার শত ঊনষাট টাকা
$text = $numto->bnMoney(13459.05);  // Output:  তেরো হাজার চার শত ঊনষাট টাকা পাঁচ পয়সা
$text = $numto->bnMoney(13459.5);   // Output:  তেরো হাজার চার শত ঊনষাট টাকা পঞ্চাশ পয়সা
```

### Number to Bangla Number

Use `bnNum()` to convert any number into bangla number. Example,

```text
$text = $numto->bnNum(13459);    // Output:  ১৩৪৫৯
$text = $numto->bnNum(2334.768); // Output:  ২৩৩৪.৭৬৮
```

### Number to Month Name in Bangla

Use `bnMonth()` to convert any number into bangla number. Input Limit \(1-12\) Example,

```text
$text = $numto->bnMonth(1);    // Output:  জানুয়ারি 
$text = $numto->bnMonth(4);    // Output:  এপ্রিল
```

### Comma separated number

Use `bnCommaLakh()` to convert any number into bangla number. Example,

```text
$text = $numto->bnCommaLakh(12121212);    // Output:  ১,২১,২১,২১২
```

## License

Number to Bangla is licensed under [The MIT License \(MIT\)]().

