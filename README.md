from datetime import datetime, timedelta

def main():
    sessions = []

    print("Study Time Calculator")
    print("Enter start and end times in HH:MM format.")
    print("Type 'done' to finish.\n")

    while True:
        start = input("Start time: ").strip()

        if start.lower() == "done":
            break

        end = input("End time: ").strip()

        try:
            start_time = datetime.strptime(start, "%H:%M")
            end_time = datetime.strptime(end, "%H:%M")

            if end_time < start_time:
                end_time += timedelta(days=1)

            duration = end_time - start_time
            minutes = int(duration.total_seconds() // 60)

            sessions.append(minutes)
            print(f"Session duration: {minutes} minutes\n")

        except ValueError:
            print("Invalid time. Use HH:MM format.\n")

    total = sum(sessions)

    print("\n--- Study Summary ---")
    print(f"Sessions: {len(sessions)}")
    print(f"Total minutes: {total}")
    print(f"Total hours: {total / 60:.2f}")

if __name__ == "__main__":
    main()
