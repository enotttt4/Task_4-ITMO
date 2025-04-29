# Task_4-ITMO

def read_data(filename):
    with open(filename, 'r') as file:
        data = []
        for line in file:
            line = line.strip()
            if line:
                value = line.replace(',', '.').split('\t')[0]
                try:
                    data.append(float(value))
                except ValueError:
                    print(f"Пропущена строка с некорректными данными: {line}")
        return data

def calculate_mean(data):
    total = 0.0
    count = 0
    for value in data:
        total += value
        count += 1
    return total / count if count != 0 else 0.0

def calculate_std_dev(data, mean):
    squared_diff_sum = 0.0
    count = 0
    for value in data:
        squared_diff_sum += (value - mean) ** 2
        count += 1
    variance = squared_diff_sum / count
    return variance ** 0.5

filename = 'CdSe_CdZnS Core_Shell.txt'
data = read_data(filename)

if not data:
    print("Файл пуст или данные отсутствуют.")
else:
    mean = calculate_mean(data)
    std_dev = calculate_std_dev(data, mean)
    print(f"Среднее значение: {mean}")
    print(f"Среднеквадратичное отклонение: {std_dev}")

