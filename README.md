Requirements:
Matplotlib,
Numpy,
Pandas

Code to create data
# Create Some Random Data For Your Vehicles
Weight = np.random.uniform(low=100, high=500, size=1000)
Colour = np.array(['red', 'blue', 'green', 'yellow', 'black', 'white', 'grey', 'purple', 'radish', 'pink'] * 100)

# Write Data to a Csv File
df = pd.DataFrame({'Weight': Weight, 'Colour': Colour})
df.to_csv('random_data_Vehicles.csv', index=False)
print(df.head())
print(len(df))

df = pd.read_csv('random_data_Vehicles.csv')


# Refer Wheels to the Vehicles according to their Weight
def wheels(row):  # Maximum Weight is 500, Lowest is 100
    if row['Weight'] < 220:
        return 2
    elif row['Weight'] <= 300:
        return 3
    else:
        return 4


df['Wheels'] = df.apply(wheels, axis=1)
df.to_csv('random_data_Vehicles.csv', index=False)
print(df.head(), df.tail())
x = pd.read_csv('random_data_Vehicles.csv')
print(x)

#Assign Height to the Vehicles
def height(row):
    if row['Wheels'] == 2:
        return np.random.randint(50, 100, size=1)
    elif row['Wheels'] == 3:
        return np.random.randint(50, 70, size=1)
    else:
        return np.random.randint(1, 50, size=1)


df['Height'] = df.apply(height, axis=1)
df.to_csv('random_data_Vehicles.csv')
print(df)
