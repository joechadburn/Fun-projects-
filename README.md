ames = ['Cuba I', 'San Felipe II Okeechobee', 'Bahamas', 'Cuba II', 'CubaBrownsville', 'Tampico', 'Labor Day', 'New England', 'Carol', 'Janet', 'Carla', 'Hattie', 'Beulah', 'Camille', 'Edith', 'Anita', 'David', 'Allen', 'Gilbert', 'Hugo', 'Andrew', 'Mitch', 'Isabel', 'Ivan', 'Emily', 'Katrina', 'Rita', 'Wilma', 'Dean', 'Felix', 'Matthew', 'Irma', 'Maria', 'Michael']

months = ['October', 'September', 'September', 'November', 'August', 'September', 'September', 'September', 'September', 'September', 'September', 'October', 'September', 'August', 'September', 'September', 'August', 'August', 'September', 'September', 'August', 'October', 'September', 'September', 'July', 'August', 'September', 'October', 'August', 'September', 'October', 'September', 'September', 'October']

years = [1924, 1928, 1932, 1932, 1933, 1933, 1935, 1938, 1953, 1955, 1961, 1961, 1967, 1969, 1971, 1977, 1979, 1980, 1988, 1989, 1992, 1998, 2003, 2004, 2005, 2005, 2005, 2005, 2007, 2007, 2016, 2017, 2017, 2018]

max_sustained_winds = [165, 160, 160, 175, 160, 160, 185, 160, 160, 175, 175, 160, 160, 175, 160, 175, 175, 190, 185, 160, 175, 180, 165, 165, 160, 175, 180, 185, 175, 175, 165, 180, 175, 160]

areas_affected = [['Central America', 'Mexico', 'Cuba', 'Florida', 'The Bahamas'], ['Lesser Antilles', 'The Bahamas', 'United States East Coast', 'Atlantic Canada'], ['The Bahamas', 'Northeastern United States'], ['Lesser Antilles', 'Jamaica', 'Cayman Islands', 'Cuba', 'The Bahamas', 'Bermuda'], ['The Bahamas', 'Cuba', 'Florida', 'Texas', 'Tamaulipas'], ['Jamaica', 'Yucatn Peninsula'], ['The Bahamas', 'Florida', 'Georgia', 'The Carolinas', 'Virginia'], ['Southeastern United States', 'Northeastern United States', 'Southwestern Quebec'], ['Bermuda', 'New England', 'Atlantic Canada'], ['Lesser Antilles', 'Central America'], ['Texas', 'Louisiana', 'Midwestern United States'], ['Central America'], ['The Caribbean', 'Mexico', 'Texas'], ['Cuba', 'United States Gulf Coast'], ['The Caribbean', 'Central America', 'Mexico', 'United States Gulf Coast'], ['Mexico'], ['The Caribbean', 'United States East coast'], ['The Caribbean', 'Yucatn Peninsula', 'Mexico', 'South Texas'], ['Jamaica', 'Venezuela', 'Central America', 'Hispaniola', 'Mexico'], ['The Caribbean', 'United States East Coast'], ['The Bahamas', 'Florida', 'United States Gulf Coast'], ['Central America', 'Yucatn Peninsula', 'South Florida'], ['Greater Antilles', 'Bahamas', 'Eastern United States', 'Ontario'], ['The Caribbean', 'Venezuela', 'United States Gulf Coast'], ['Windward Islands', 'Jamaica', 'Mexico', 'Texas'], ['Bahamas', 'United States Gulf Coast'], ['Cuba', 'United States Gulf Coast'], ['Greater Antilles', 'Central America', 'Florida'], ['The Caribbean', 'Central America'], ['Nicaragua', 'Honduras'], ['Antilles', 'Venezuela', 'Colombia', 'United States East Coast', 'Atlantic Canada'], ['Cape Verde', 'The Caribbean', 'British Virgin Islands', 'U.S. Virgin Islands', 'Cuba', 'Florida'], ['Lesser Antilles', 'Virgin Islands', 'Puerto Rico', 'Dominican Republic', 'Turks and Caicos Islands'], ['Central America', 'United States Gulf Coast (especially Florida Panhandle)']]

damages = ['Damages not recorded', '100M', 'Damages not recorded', '40M', '27.9M', '5M', 'Damages not recorded', '306M', '2M', '65.8M', '326M', '60.3M', '208M', '1.42B', '25.4M', 'Damages not recorded', '1.54B', '1.24B', '7.1B', '10B', '26.5B', '6.2B', '5.37B', '23.3B', '1.01B', '125B', '12B', '29.4B', '1.76B', '720M', '15.1B', '64.8B', '91.6B', '25.1B']

deaths = [90,4000,16,3103,179,184,408,682,5,1023,43,319,688,259,37,11,2068,269,318,107,65,19325,51,124,17,1836,125,87,45,133,603,138,3057,74]

conversion = {"M": 1000000,
              "B": 1000000000}

# test function by updating damages
updated_damage_list = []
def updated_list(damage_list):
  for update in damage_list:
    if update[-1] in conversion:
      updated_damage_list.append(float(update[:-1]) * conversion[update[-1]])
    else:
      updated_damage_list.append(update)
  return updated_damage_list
updated_damage = updated_list(damages)
# print (updated_damage)

# Create a Table
#I have the hurricane data in the right place its just a matter of itterating through all of the names-deaths and producing a table
def hurricane_zip(name, month, year, winds, areas, damage, death):
  data_hurricane_zip_list = list(zip(name, month, year, winds, areas, death))
  return data_hurricane_zip_list
hurricane_zip(names, months, years, max_sustained_winds, areas_affected, damages, deaths)

def hurricane_data(names, months, years, max_sustained_winds, areas_affected, damages, deaths):
    data_hurricane_zip_list = list(zip(names, months, years, max_sustained_winds, areas_affected, deaths))
    hurricane_data_list = []
    for indexes in range(len(data_hurricane_zip_list)):
        hurricane_data_dict = {"Name": names[indexes], "Month": months[indexes], "Year": years[indexes], "Max Sustained Wind": max_sustained_winds[indexes], "Areas Affected": areas_affected[indexes], "Damage": updated_damage[indexes], "Deaths": deaths[indexes]}
        hurricane_data_list.append(hurricane_data_dict) 
    return hurricane_data_list 

hurricane_info = hurricane_data(names, months, years, max_sustained_winds, areas_affected, damages, deaths)
print(hurricane_info)

#years as keys variable:
years_dict = dict(zip(years, hurricane_info))

# I want to remove the tuples from the list so it can count every element in the list and put the element as a key and the count as a value,

#The problem is that my output has a list of tuples and it counts by tuples instead of each individule element in the list. However this function should work when i remove said tuples:

#now the problem is that I need to figure out how i can change the key without giving me a key error.
print('                                                                 ')
new_areas_affected_list = []
areas_affected_tuple = [tuple(x) for x in areas_affected]
#count and add to dictionary functiom 
#This took me FOOOOOOOREEEEVEEEER
for elements in areas_affected_tuple:
    for item in elements:
      new_areas_affected_list.append(item)  
def damage_occurrence(areas):
  area_affected_dict = {}
  for count in areas:
    if count in area_affected_dict:
      area_affected_dict[count] += 1
    else:
      area_affected_dict[count] = 1
  return area_affected_dict
print("This is how many times each area got hit: " + str(damage_occurrence(new_areas_affected_list)))

affected_areas_count = damage_occurrence(new_areas_affected_list)
print('                                                               ')
#Max affected area function 
def affected_area_max(count):
   for key, value in count.items():
    max_areas_affected = max(count,key=count.get)
    values = max(count.values())
    return (max_areas_affected + ': ' + str(values) + " hits")
max_affected_area = affected_area_max(affected_areas_count)
print("The most affected area is " + (max_affected_area))
print('                                                 ')

#deadliest hurricane function
def find_deadliest_hurricane(hurricane_info):
    max_deaths = 0
    deadliest_hurricane = None

    for hurricane in hurricane_info:
        deaths = hurricane["Deaths"]
        if deaths > max_deaths:
            max_deaths = deaths
            deadliest_hurricane = hurricane["Name"]

    return deadliest_hurricane, max_deaths
deadliest_hurricane_name, max_death_count = find_deadliest_hurricane(hurricane_info)
print(f"The deadliest hurricane is {deadliest_hurricane_name} with {max_death_count} deaths and these are the Hurricanes in order least to most deadly: ")
#death mortality rating function
def mortality_of_hurricane(hurricane):
    mortality_scale = {0: 0, 1: 100, 2: 500, 3: 1000, 4: 10000}
    name = hurricane['Name']
    rating = hurricane['Deaths']

    if rating <= 0:
        return f"{name} had no deaths"
    elif rating <= 100:
        return f"{name} is rated a 1"
    elif rating <= 500:
        return f"{name} is rated a 2"
    elif rating <= 1000:
        return f"{name} is rated a 3"
    elif rating <= 10000:
        return f"{name} is rated a 4"
    else:
        return f"{name} has an extreme death toll"
hurricane_ratings_dict = {}
for hurricane in hurricane_info:
    rating = mortality_of_hurricane(hurricane)
    if rating.startswith("This hurricane"):
        continue  # Skip hurricanes with no deaths
    rating_key = rating.split()[-1]  # Extract the numeric rating
    if rating_key not in hurricane_ratings_dict:
        hurricane_ratings_dict[rating_key] = []
    hurricane_ratings_dict[rating_key].append(hurricane['Name'])
# clean look:
print("Hurricane Ratings (Rating: Names):")
for rating, names in hurricane_ratings_dict.items():
    print(f"{rating}: {', '.join(names)}")

#Find how much the areas with the most damage cost:
damage_scale = {0: 0,
                1: 100000000,
                2: 1000000000,
                3: 10000000000,
                4: 50000000000}
list_of_damage_int = []
for _int_list in updated_damage:
  try:
    list_of_damage_int.append(int(_int_list))
  except ValueError:
    list_of_damage_int.append(0)
#dictionary of keys, area and how much it cost
names_and_damages_dict = dict(zip(new_areas_affected_list, list_of_damage_int))
# print(names_and_damages_dict)

#This one was somehow painfully hard, even though I eventually broke and looked at other peoples code, mine was so different that i had to come up with a completly different algoritham. This one and section 5 counting the amount of times each area got hit took me hours and hours of research. Finally I finished. 
def damage_in_hurricanes(hurricanes, scale):
  hurricanes_by_damage = {}
  for keys in scale:
    hurricanes_by_damage[keys] = []
  for key, damage in hurricanes.items():
      if damage <= scale[0]:
        hurricanes_by_damage[0].append(key)
        hurricanes_by_damage[0].append(damage)
      elif damage <= scale[1]:
        hurricanes_by_damage[1].append(key)
        hurricanes_by_damage[1].append(damage)
      elif damage <= scale[2]:
        hurricanes_by_damage[2].append(key)
        hurricanes_by_damage[2].append(damage)
      elif damage <= scale[3]:
        hurricanes_by_damage[3].append(key)
        hurricanes_by_damage[3].append(damage)
      elif damage <= scale[4]:
        hurricanes_by_damage[4].append(key)
        hurricanes_by_damage[4].append(damage)
  return hurricanes_by_damage
hurricane_damage_by_scale = damage_in_hurricanes(names_and_damages_dict, damage_scale)
print('                                                                ')
print('0 Means the damage is "Unknown". This is how much damge by scale each hurricane caused: ' + str(hurricane_damage_by_scale))
