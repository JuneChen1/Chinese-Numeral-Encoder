# Codewars- Chinese Numeral Encoder (Javascript)

```
function toChineseNumeral(num){
  const numerals = {
    "-":"负",
    ".":"点",
    0:"零",
    1:"一",
    2:"二",
    3:"三",
    4:"四",
    5:"五",
    6:"六",
    7:"七",
    8:"八",
    9:"九",
    10:"十",
    100:"百",
    1000:"千",
    10000:"万"
  };
  
  let [integer, decimal] = num.toString().split(".");
  let result = "";

  if (integer.startsWith("-")) {
    result += numerals["-"];
    integer = integer.slice(1);
  }
  
  if (integer === "0") {
    result += numerals[0];
  } else {
    integer.split('').map(n => Number(n)).forEach((n, i) => {
      const digit = integer.length - i - 1;
      
      if (n === 0 && (Number(integer[i + 1]) === 0 || digit === 0)) return
      
      if (n === 1 && integer.length === 2 && digit === 1) {
        result += numerals[10];
        return
      }
      
      result += numerals[n];
      
      if (n === 0) return

      if (digit === 4) {
        result += numerals[10000];
      } else if (digit === 3) {
        result += numerals[1000];
      } else if (digit === 2) {
        result += numerals[100];
      } else if (digit === 1) {
        result += numerals[10];
      }
    });
  }
  
  if (decimal) {
    result += numerals["."];
    decimal.split('').forEach(n => result += numerals[n]);
  }
  
  return result;
}
```
[KATA](https://www.codewars.com/kata/52608f5345d4a19bed000b31/javascript)
