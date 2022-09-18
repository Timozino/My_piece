class RomanNumerals:
    sym = ['M', 'CM', 'D', 'CD', 'C', 'XC', 'L', 'XL', 'X', 'IX', 'V', 'IV', 'I']
    num = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]

    @staticmethod
    def to_roman(number):
        result = ''
        pointer = 0
        while number:
            div = number // RomanNumerals.num[pointer]
            number %= RomanNumerals.num[pointer]
            while div:
                result += RomanNumerals.sym[pointer]
                div -= 1
            pointer += 1
        return result

    @staticmethod
    def from_roman(roman_numeral):
        result = 0
        for idx, val in enumerate(roman_numeral):
            first_num = RomanNumerals.num[RomanNumerals.sym.index(val)]
            second_num = RomanNumerals.num[RomanNumerals.sym.index(roman_numeral[idx + 1])] if idx + 1 != len(
                roman_numeral) else -1
            if first_num >= second_num:
                result += first_num
            else:
                result -= first_num
        return result