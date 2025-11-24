import os
import datetime
import curses
import random
import json
import psutil
import GPUtil
import time

# Made by Katt, improved by Yazin Tantawi

# Persistent storage for installed apps
INSTALLED_APPS_FILE = "installed_apps.json"
installed_apps = {"snake": False}


# Utility Functions
def save_installed_apps():
    with open(INSTALLED_APPS_FILE, "w") as f:
        json.dump(installed_apps, f)


def load_installed_apps():
    global installed_apps
    if os.path.exists(INSTALLED_APPS_FILE):
        with open(INSTALLED_APPS_FILE, "r") as f:
            installed_apps.update(json.load(f))


# Command Functions
def print_welcome_message():
    print(
        """
 ___    ____  ____    _____  ____  ____  ____    __   ____  ____  _  _  ___ 
/ __)  (  _ \(_  _)  (  _  )(  _ \( ___)(  _ \  /__\ (_  _)(_  _)( \( )/ __)
\__ \   )___/ _)(_    )(_)(  )___/ )__)  )   / /(__)\  )(   _)(_  )  (( (_-.
(___/()(__)()(____)  (_____)(__)  (____)(_)\_)(__)(__)(__) (____)(_)\_)\___/
 ___  _  _  ___  ____  ____  __  __                                         
/ __)( \/ )/ __)(_  _)( ___)(  \/  )                                        
\__ \ \  / \__ \  )(   )__)  )    (                                         
(___/ (__) (___/ (__) (____)(_/\/\_)                                        


        Welcome to the Simplified Python Imitation OS (SPIOS)
        Type 'help' to see a list of commands.
        Type 'exit' to quit.
        """
    )


def print_command_list():
    print("\nAvailable Commands:")
    print("1. ls - List files in the current directory")
    print("2. cd [directory] - Change directory")
    print("3. date - Display the current date and time")
    print("4. snake - Play the Snake game")
    print("5. help - Show this command list")
    print("6. exit - Quit the system")
    print("7. edit [filename] - Create or edit a file")
    print("8. save - Save changes to the current file")
    print("9. rename [old_filename] [new_filename] - Rename a file")
    print("10. computerinfo - Display computer information")

def list_files():
    try:
        files = os.listdir(os.getcwd())
        print("\n".join(files) if files else "No files in the current directory.")
    except Exception as e:
        print(f"Error listing files: {e}")


def change_directory(directory):
    try:
        os.chdir(directory)
        print(f"Changed directory to: {os.getcwd()}")
    except Exception as e:
        print(f"Error changing directory: {e}")


def display_date():
    now = datetime.datetime.now()
    print(f"Current date and time: {now.strftime('%Y-%m-%d %H:%M:%S')}")


def install_snake():
    if not installed_apps["snake"]:
        installed_apps["snake"] = True
        save_installed_apps()
        print("Snake game installed successfully!")
    else:
        print("Snake game is already installed.")


def play_snake(stdscr):
    curses.curs_set(0)
    sh, sw = stdscr.getmaxyx()
    w = curses.newwin(sh, sw, 0, 0)
    w.keypad(1)
    w.timeout(100)

    # Snake setup
    snk_x = sw // 4
    snk_y = sh // 2
    snake = [[snk_y, snk_x], [snk_y, snk_x - 1], [snk_y, snk_x - 2]]
    food = [sh // 2, sw // 2]
    w.addch(food[0], food[1], curses.ACS_PI)

    key = curses.KEY_RIGHT
    while True:
        next_key = w.getch()
        key = key if next_key == -1 else next_key

        # New head position
        head = [snake[0][0], snake[0][1]]
        if key == curses.KEY_DOWN:
            head[0] += 1
        if key == curses.KEY_UP:
            head[0] -= 1
        if key == curses.KEY_LEFT:
            head[1] -= 1
        if key == curses.KEY_RIGHT:
            head[1] += 1

        snake.insert(0, head)

        # Check for collisions
        if (
            snake[0][0] in [0, sh]
            or snake[0][1] in [0, sw]
            or snake[0] in snake[1:]
        ):
            break

        # Check if food eaten
        if snake[0] == food:
            food = None
            while food is None:
                nf = [random.randint(1, sh - 2), random.randint(1, sw - 2)]
                food = nf if nf not in snake else None
            w.addch(food[0], food[1], curses.ACS_PI)
        else:
            tail = snake.pop()
            w.addch(tail[0], tail[1], " ")

        w.addch(snake[0][0], snake[0][1], curses.ACS_CKBOARD)

    stdscr.addstr(sh // 2, sw // 2 - 5, "Game Over!")
    stdscr.refresh()
    time.sleep(2)


def snake_game():
    if installed_apps["snake"]:
        curses.wrapper(play_snake)
    else:
        print("Snake game is not installed. Type 'install snake' to install it.")

def get_computer_info():
    try:
        # CPU info
        cpu_cores = psutil.cpu_count(logical=True)
        cpu_freq = psutil.cpu_freq()
        cpu_speed = cpu_freq.max if cpu_freq else "Unknown"

        # Memory info
        memory_info = psutil.virtual_memory()
        total_memory = memory_info.total // (1024 ** 2)  # in MB

        # GPU info
        gpus = GPUtil.getGPUs()
        if gpus:
            gpu_info = [f"{gpu.name} (Memory Free: {gpu.memoryFree}MB, Memory Total: {gpu.memoryTotal}MB)" for gpu in gpus]
        else:
            gpu_info = ["No GPU detected"]

        print(f"CPU Cores: {cpu_cores}")
        print(f"CPU Max Speed: {cpu_speed / 1000} GHz")  # Convert from MHz to GHz
        print(f"RAM: {total_memory} MB")
        print("GPU Info:")
        for info in gpu_info:
            print(f"  - {info}")

    except Exception as e:
        print(f"An error occurred while retrieving computer info: {e}")

def display_date():
    now = datetime.datetime.now()
    print(f"Current date and time: {now.strftime('%Y-%m-%d %H:%M:%S')}")

def edit_file(filename):
    global current_file
    current_file = filename
    print(f"Editing file: {filename}")
    if os.path.exists(filename):
        with open(filename, 'r') as file:
            print(file.read())
    else:
        print("New file. Start typing to create content.")

def save_file():
    global current_file
    if current_file is None:
        print("No file is open. Use 'edit [filename]' to open a file first.")
        return
    
    content = input("Enter the content to save (end with a single dot on a new line):\n")
    if content.strip() == ".":
        print("Empty content. File not saved.")
        return
    
    with open(current_file, 'w') as file:
        file.write(content)
    print(f"File '{current_file}' saved.")

def rename_file(old_filename, new_filename):
    try:
        os.rename(old_filename, new_filename)
        print(f"File renamed from '{old_filename}' to '{new_filename}'")
    except FileNotFoundError:
        print(f"File {old_filename} not found.")
    except Exception as e:
        print(f"An error occurred while renaming the file: {e}")


# Main Program
def main():

    global current_file
    current_file = None

    load_installed_apps()
    print_welcome_message()

    while True:
        command = input("\n> ").strip().lower()

        if command == "exit":
            print("Goodbye!")
            break
        elif command == "help":
            print_command_list()
        elif command == "ls":
            list_files()
        elif command.startswith("cd "):
            change_directory(command[3:])
        elif command == "date":
            display_date()
        elif command == "install snake":
            install_snake()
        elif command == "snake":
            snake_game()
        elif command == 'computerinfo':
            get_computer_info()
        elif command == 'date':
            display_date()
        elif command == 'ls':
            list_files(os.getcwd())
        elif command.startswith('edit '):
            filename = command[5:].strip()
            edit_file(filename)
        elif command == 'save':
            save_file()
        elif command.startswith('rename '):
            parts = command.split(' ', 2)
            if len(parts) < 3:
                print("Usage: rename [old_filename] [new_filename]")
            else:
                old_filename = parts[1].strip()
                new_filename = parts[2].strip()
                rename_file(old_filename, new_filename)
        else:
            print("Unknown command. Type 'help' for a list of commands.")

    

if __name__ == "__main__":
    main()
