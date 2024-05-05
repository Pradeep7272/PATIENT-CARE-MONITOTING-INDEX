# PATIENT-CARE-MONITOTING-INDEX
import matplotlib.pyplot as plt

# Function to input visit counts for each staff member to each patient room
def input_visits(room_names):
    visits = {'Doctor': [], 'Nurse': [], 'Cleaning Staff': []}
    for room in room_names:
        print(f"Enter visit counts for {room}:")
        for staff in visits:
            visit_count = int(input(f"Enter number of visits by {staff}: "))
            visits[staff].append(visit_count)
    return visits

# Function to plot the bar graph
def plot_bar_graph(visits):
    room_names = [f"Room {i+1}" for i in range(len(visits['Doctor']))]
    staff_labels = list(visits.keys())
    num_staff = len(staff_labels)

    fig, ax = plt.subplots(figsize=(10, 6))

    bar_width = 0.2
    index = range(len(room_names))
    for i, staff in enumerate(staff_labels):
        ax.bar([p + i * bar_width for p in index], visits[staff], bar_width, label=staff)

    ax.set_xlabel('Patient Rooms')
    ax.set_ylabel('Number of Visits')
    ax.set_title('Visits by Staff to Patient Rooms')
    ax.set_xticks([p + 0.5 * bar_width * (num_staff - 1) for p in index])
    ax.set_xticklabels(room_names)
    ax.legend()

    plt.show()

# Main function
def main():
    room_names = ['Room 1', 'Room 2', 'Room 3']
    visits = input_visits(room_names)
    plot_bar_graph(visits)

if __name__ == "__main__":
    main()
