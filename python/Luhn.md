# Luhn.py - Class
```python
class Luhn:

    def pass_luhn(self, acct):
        """
        Returns True if acct passes the Luhn algorithm check
        or False if it does not
        """
        if acct.isnumeric() is False:
            return False
        sum = 0
        for x in acct[-1::-2]:
            sum += int(x)
        for x in acct[-2::-2]:
            for y in str(int(x) * 2):
                sum += int(y)
        return sum % 10 == 0
    
    def is_amex(self, acct):
        """
        Returns True if acct passes Luhn and is also a valid
        American Express number
        """
        if self.pass_luhn(acct) and len(acct) == 15:
            if acct[:2] == '34' or acct[0:2] == '37':
                return True
        return False

    def is_visa(self, acct):
        """
        Returns True if acct passes Luhn and is also a valid
        Visa number
        """
        if self.pass_luhn(acct) and acct[:1] == '4':
            if len(acct) == 13 or len(acct) == 16:
                return True
        return False

    def is_mastercard(self, acct):
        """
        Returns True if acct passes Luhn and is also a valid
        MasterCard number, or False if not
        """
        return self.pass_luhn(acct) and len(acct) == 16 and int(acct[:2]) >= 51 and int(acct[:2]) <= 55

    def is_discover(self, acct):
        """
        Returns True if acct passes Luhn and is also a valid
        Discover number, or False if not
        """
        return self.pass_luhn(acct) and len(acct) == 16 and acct[:4] == '6011'

    def is_valid_cc(self, acct):
        """
        Returns True if acct is any valid credit card number 
        or False if not
        """
        return self.is_visa(acct) or self.is_mastercard(acct) or self.is_amex(acct) or self.is_discover(acct)
```

# Credit Cards and the Luhn Algorithm

## About Luhn
The Luhn algorithm is a simple checksum used to verify credit card numbers. For an account number to pass the Luhn test it must:
- From the rightmost digit moving left, double the value of every second digit. If the result of doubling is > 9 then sum the digits. e.g., 7x2 = 14, 1+4=5
- Take the sum of all digits
- Divide the sum by 10. To pass the Luhn test the remainder from dividing by 10 must be zero

## The Lab
1. Implement the pass_luhn method. It should return True if the string of numbers passes the algorithm described above or False if not.
2. Implement the is_visa method. An account number is a valid Visa if it is either 13 or 16 numbers long, starts with a 4, and passes the Luhn test.
3. Implement the is_mastercard method. An account number is a valid MasterCard if it is 16 characters long; starts with a number in the range 51-55 inclusive; and passes the Luhn test.
4. Implement the is_amex method. An account is a valid American Express if it is 15 characters long, starts with either a 34 or 37, and passes the Luhn test.
5. Implement the is_discover method. An account number is a valid Discover if it is 16 characters long, starts with 6011, and passes the Luhn test.
6. Implement the is_valid_cc method. It should return True if it is valid for any of the 4 other is_X methods or False if not.
