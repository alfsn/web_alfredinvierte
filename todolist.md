# Todo

## Cuestionario:
https://gemini.google.com/app/53a30cd230d2ea75

1. hacer que la logica del cuestionario me devuelva un espacio 3d que me de distintos tipos de clientes. El espacio podria ser de 

X-Axis: Capital Power (Capacity)

    Inputs: Income flow, Financial Toolkit (Savings/Brokerage).

    Range: 0 (Broke) to 10 (Flush).

Y-Axis: Emotional Stability (Temperament)

    Inputs: Market Drop reaction, Checking frequency.

    Range: 0 (Neurotic) to 10 (Stoic).

Z-Axis: Horizon (Time)

    Inputs: Time Horizon question.

    Range: 0 (Tomorrow) to 10 (Decades).

This is the correct intuition. Offloading the "math" to your Astro frontend (JavaScript) is significantly better than building a spaghetti-logic tree inside Make.com.

By doing the math in the browser, your form will simply send Netlify a final "Result Code" (e.g., ARCHITECT or TRADER), and Make.com just has to look at that code and pick the matching email template.