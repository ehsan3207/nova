# پروتوکل های پروژه

!!! warning "پروتوکل های پروژه"
    رعایت این قوانین برای تمامی اعضای تیم **الزامی** است.  
   هدف، ایجاد یک ساختار استاندارد، قابل‌نگهداری و توسعه‌پذیر است.


!!! note ""


## Git و مستندسازی

نام `commit` باید واضح و استاندارد باشد:

`feat:` برای ویژگی جدید

`fix:` برای رفع باگ

`refactor:` برای بازنویسی بدون تغییر رفتار

`docs:` برای تغییر مستندات

مثال:

```bash

feat(users): add user registration endpoint

fix(auth): resolve token refresh issue

refactor(core): simplify validation logic

docs(api): update usage examples

!!! note ""

## Front-end


درون هر تابع باید کارایی آن تابع مشخص شود مانند مثال زیر:



```js


function factorial(n) {
    /*
        * This function calculates the factorial of a given number.
        * The factorial of a number (n!) is the product of all positive integers less than or equal to n.
        * 
        * Example:
        * factorial(5) = 5 * 4 * 3 * 2 * 1 = 120
        * 
        * Steps:
        * 1. Check if the input number is less than 0 → return null (because factorial is not defined for negative numbers)
        * 2. If the number is 0 or 1 → return 1 (base case)
        * 3. Otherwise, multiply the number by the factorial of (number - 1) recursively.
    */


    if (n < 0) {
        return null; // factorial is not defined for negative numbers
    } else if (n === 0 || n === 1) {
        return 1; // base case
    } else {
        return n * factorial(n - 1); // recursive call
    }
}

// Example usage:
console.log(factorial(5)); // Output: 120

```

### ساختار کلی پروژه
پوشه‌ها و فایل‌ها باید به صورت PascalCase نوشته شود , برای نمونه:

`UserProfile.jsx`

`HomePage.jsx`

`NavBar.jsx`

---

متغیر ها باید به صورت `camelCase` باشند , برای مثال:

`let userProfile = null`

`let homePage = null`

`let navBar = null`

---

> کدهای تکراری (duplicate logic) را در فایل جدا (`utils/`) قرار دهید.

---
از `async/await` به جای `then/catch` استفاده کنید.

```js
const data = await getData();

```

---
از error handling مناسب استفاده کنید.

```js
try {
  await doSomething();
} catch (error) {
  console.error("Error:", error);
}


```

---

> از `ESLint` و `Prettier` استفاده کنید تا فرمت کدها خودکار یکسان بماند.



---

## API Routes / Server Actions

> نکته: هر Route فقط باید یک مسئولیت مشخص داشته باشد
و پاسخ‌ها به‌صورت JSON ساختار‌یافته برگردانده شوند.

---

!!! note ""


## Back-end 

###  توضیح درون توابع و Viewها

درون هر تابع، متد یا View باید **کارایی و هدف آن** به‌صورت کامنت چندخطی انگلیسی مشخص شود.  
نمونه صحیح :


```python
def calculate_discount(price: float, discount: float) -> float:
    """
    This function calculates the final price after applying a discount.
    
    Args:
        price (float): Original price of the product.
        discount (float): Discount percentage (0–100).

    Returns:
        float: Final price after applying the discount.

    Example:
        calculate_discount(100, 20) → 80.0
    """

    if discount < 0 or discount > 100:
        raise ValueError("Discount must be between 0 and 100")

    final_price = price - (price * (discount / 100))
    return round(final_price, 2)

```


## ساختار کلی پروژه


فایل‌ها و ماژول‌ها باید با `snake_case` نام‌گذاری شوند.

کلاس‌ها و مدل‌ها با `PascalCase` نوشته شوند.

مثال:


`models.py`

`views.py`

`serializers.py`

`urls.py`

---
نام‌گذاری متغیرها و توابع:

متغیرها و توابع با `snake_case`

کلاس‌ها با `PascalCase`

ثابت‌ها (`constants`) با `UPPER_CASE`

مثال:

```python

user_profile = None
def get_user_data():
    ...
class UserProfile:
    ...
MAX_UPLOAD_SIZE = 10485760
```


### منطق تکراری
> هر منطق تکراری باید در مسیر جداگانه‌ای مثل utils/ یا services/ نگهداری شود.

### اصول نوشتن APIها
> پاسخ API باید ساختاریافته و ثابت باشد.


### تنظیمات و Config
> همه تنظیمات حساس در .env ذخیره شوند.

### استانداردهای کدنویسی
>از Black و isort برای فرمت خودکار کد استفاده کنید.


>نام متغیرها باید توصیفی و معنادار باشند.

>هیچ فانکشن یا کلاس بدون Docstring وجود نداشته باشد.



---
