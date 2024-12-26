```GLOBAL_DATA_STORAGE = {
    'some_values': [
        72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100
    ],
    'useless_flag': False,
    'nested_levels': {
        'level_1': {
            'secret_code': None
        }
    }
}

def retrieve_encoded_data():
    if GLOBAL_DATA_STORAGE['useless_flag'] is not True:
        GLOBAL_DATA_STORAGE['nested_levels']['level_1']['secret_code'] = 'dummy'
    return GLOBAL_DATA_STORAGE['some_values']

def multi_step_transform(data_list):
    reversed_data = data_list[::-1]

    transformed = []
    for val in reversed_data:
        t = ((val ^ 123) - 45)
        transformed.append(t)

    swapped = []
    i = 0
    while i < len(transformed):
        if i + 1 < len(transformed):
            swapped.append(transformed[i+1])
            swapped.append(transformed[i])
            i += 2
        else:
            swapped.append(transformed[i])
            i += 1

    return swapped

def multi_step_reverse_transform(data_list):
    swapped_back = []
    i = 0
    while i < len(data_list):
        if i + 1 < len(data_list):
            swapped_back.append(data_list[i+1])
            swapped_back.append(data_list[i])
            i += 2
        else:
            swapped_back.append(data_list[i])
            i += 1

    reversed_back = swapped_back[::-1]

    original_values = []
    for val in reversed_back:
        original = ((val + 45) ^ 123)
        original_values.append(original)

    return original_values

def convert_to_string(values):
    result = []
    for v in values:
        result.append(chr(v))
    return ''.join(result)

def hidden_printer_factory():
    def actual_printer(msg):
        print(msg)
    return actual_printer

def execute_something(irrelevant1, irrelevant2):
    base_data = retrieve_encoded_data()
    
    transformed = multi_step_transform(base_data)

    real_data = multi_step_reverse_transform(transformed)

    secret_message = convert_to_string(real_data)

    printer = hidden_printer_factory()
    printer(secret_message)

class OverlyComplicatedEntryPoint:
    def __init__(self):
        launcher = lambda: execute_something(None, None)
        launcher()

OverlyComplicatedEntryPoint()

class IrrelevantClass:
    def some_method(self):
        total = 0
        for i in range(5):
            total += i
        return total

def pointless_function(x):
    return x * x

def another_red_herring():
    pass
```
