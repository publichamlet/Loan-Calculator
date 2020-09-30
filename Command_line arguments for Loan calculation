import argparse
import sys
from math import ceil
from math import floor
from math import log

def error(count_None, count_neg):
    if l_p == None: count_None += 1
    elif l_p < 0: count_neg += 1
    if b.type == None: count_None += 1
    if m_p == None: count_None += 1
    elif m_p < 0: count_neg += 1
    if l_i == None: count_None += 1
    elif l_i < 0: count_neg += 1
    if n_p == None: count_None += 1
    elif n_p < 0: count_neg += 1
    if count_None > 1 or count_neg >0:
        #print(count_None, count_neg)
        print('Incorrect parameters.')
        sys.exit()


a = argparse.ArgumentParser(description='Loan Calculator', argument_default=None)

a.add_argument('--type', help='Enter the type of payment(Differentiated or Annuity)')
a.add_argument('--principal', help='Principal Amount', type=float)
a.add_argument('--payment', help='Annuity Payment', type=float)
a.add_argument('--periods', help='Loan period in months', type=float)
a.add_argument('--interest', help='Interest of Loan', type=float)

b = a.parse_args()

l_p = b.principal
m_p = b.payment
l_i = b.interest
n_p = b.periods

error(0, 0)

i = l_i / (12 * 100)

if b.type == 'annuity':
    if b.periods == None:

        y = m_p / (m_p - i * l_p)
        n = log(y, i + 1)
        n = ceil(n)
        if n == 1:
            print(f'It will take {1} month to repay this loan!')
            print(f'Overpayment = {(int((n * m_p) - l_p)):,}')
        elif n // 12 == 0:
            print(f'It will take {int(n)} months to repay this loan!')
            print(f'Overpayment = {(int((n * m_p) - l_p)):,}')
        elif n // 12 == 1:
            print(f'It will take {1} year to repay this loan!')
            print(f'Overpayment = {(int((n * m_p) - l_p)):,}')
        elif n % 12 == 0:
            print(f'It will take {int(n / 12)} years to repay this loan!')
            print(f'Overpayment = {(int((n * m_p) - l_p)):,}')
        else:
            print(f'It will take {int(n / 12)} years and {int(n % 12)} months to repay this loan!')
            print(f'Overpayment = {(int((n * m_p) - l_p)):,}')

    if b.payment == None:

        y = pow(i + 1, n_p)
        m_p = (y * i * l_p) / (y - 1)
        m_p = ceil(m_p)

        print(f'Your annuity payment = {m_p:,}!')
        print(f'Overpayment = {(int((m_p * n_p) - l_p)):,}')

    if b.principal == None:
 
        y = pow(i + 1, n_p)
        l_p = floor((m_p * (y - 1)) / (y * i))
        print(f'Your loan principal = {l_p:,}!')
        print(f'Overpayment = {(int((m_p * n_p) - l_p)):,}')

elif b.type == 'diff':
        
    t_diff = 0

    for m in range(1, int(n_p) + 1):
        D = ceil((l_p / n_p) + (i * (l_p - (l_p * (m - 1) / n_p))))
        t_diff += D
        print(f'Month {m}: payment is {D:,}')
            
    print(f'\nOverpayment = {int(t_diff - l_p):,}')
