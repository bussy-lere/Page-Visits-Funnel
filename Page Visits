import pandas as pd

visits = pd.read_csv('visits.csv',
                     parse_dates=[1])
cart = pd.read_csv('cart.csv',
                   parse_dates=[1])
checkout = pd.read_csv('checkout.csv',
                       parse_dates=[1])
purchase = pd.read_csv('purchase.csv',
                       parse_dates=[1])                     

# print(visits.head())
# print(cart.head())
# print(checkout.head())
# print(purchase.head())

visits_cart = pd.merge(visits, cart, how= 'left')

null_cart_rows = len(visits_cart[visits_cart.cart_time.isnull()])
print(len(visits_cart))

percent_null_cart = float(null_cart_rows) / len(visits_cart)
print(percent_null_cart)

cart_checkout= pd.merge(cart, checkout, how= 'left')

null_checkout_rows = len(cart_checkout[cart_checkout.checkout_time.isnull()])
print(len(cart_checkout))

percent_null_checkout = float(null_checkout_rows) / len(cart_checkout)
print(percent_null_checkout)

all_data = visits.merge(cart, how = 'left').merge(checkout, how = 'left').merge(purchase, how = 'left')
checkout_not_purchase = all_data[~(all_data.checkout_time.isnull()) & (all_data.purchase_time.isnull())]
percent_checkout_not_purchase = len(checkout_not_purchase) / float(len(all_data))

print(percent_checkout_not_purchase )

all_data['time_to_purchase'] = \
    all_data.purchase_time - \
    all_data.visit_time
print(all_data.time_to_purchase)
print(all_data.time_to_purchase.mean())
