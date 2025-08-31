---
title: Code
---

{% tabs %}
{% tab title="Ruby" %}
<pre class="language-ruby"><code class="lang-ruby"><strong>puts "こんにちは".index('に')
</strong><strong># Output: 2
</strong></code></pre>
{% endtab %}

{% tab title="Java" %}
```java
System.out.println("こんにちは".indexOf("に"));
// Output: 2
```
{% endtab %}

{% tab title="Python" %}
```python
print("こんにちは".find("に"))
# Output: 2
```
{% endtab %}

{% tab title="C" %}
```c
#include <string.h>

char str[] = "こんにちは";
char ch = 'に';
char *ptr = strchr(str, ch);

if (ptr != NULL) {
    int index = ptr - str;
    printf("%d", index);
} else {
    printf(-1);
}
//Output: 2
```
{% endtab %}
{% endtabs %}
