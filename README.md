# Loan-Calculator through a command line argument
Loan Calculator:

Calculation of differentiated payments.
To do this, the user can run the program specifying interest, number of monthly payments, and loan principal.

Ability to calculate the same values for annuity payment (principal, number of monthly payments, and monthly payment amount).

The user specifies all the known parameters with command-line arguments, and one parameter will be unknown.
This is the value the user wants to calculate.

Handling of invalid parameters.

It's a good idea to show an error message if the user enters invalid parameters (they are discussed in detail below).

The final version of your program is supposed to work from the command line and parse the following parameters:

    --type indicates the type of payment: "annuity" or "diff" (differentiated).
    If --type is specified neither as "annuity" nor as "diff" or not specified at all, show the error message.

    --payment is the monthly payment amount.
    For --type=diff, the payment is different each month,
    so we can't calculate months or principal, therefore a combination with --payment is invalid, too:

    --principal is used for calculations of both types of payment.
    You can get its value if you know the interest, annuity payment, and number of months.

    --periods denotes the number of months needed to repay the loan.
    It's calculated based on the interest, annuity payment, and principal.

    --interest is specified without a percent sign.
    Note that it can accept a floating-point value.
    Our loan calculator can't calculate the interest, so it must always be provided.
    These parameters are incorrect because --interest is missing:

You may have noticed that for differentiated payments you will need 4 out of 5 parameters (excluding payment),
and the same is true for annuity payments
(the user will be calculating the number of payments, the payment amount, or the loan principal).
Thus, you should also display an error message when fewer than four parameters are provided:

You should also display an error message when negative values are entered:

The only thing left is to compute the overpayment: the amount of interest paid over the whole term of the loan.

