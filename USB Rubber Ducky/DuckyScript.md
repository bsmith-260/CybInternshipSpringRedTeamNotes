## Ducky Script

`DuckyScript` began as a simple programming language with only three commands that could be learned within minutes. Today, it is in version 3.0, it is a feature loaded and structured programming language. It is capable of complex attacks, while being relatively simple still.

In the RubberDucky, the payload is compiled within [[Hak5 Payload Studio Pro]]. Within PayloadStudio, the DuckyScript language offers many capabilities that a usual programming language offers.

## Comments 
REM  
The `REM` command marks the rest of the line as a comment. Anything after `REM` is ignored and not executed.  
  
REM_BLOCK  
Starts a multi-line comment block. Everything between `REM_BLOCK` and `END_REM` is treated as a comment, so you don’t need `REM` on each line.  
  
END_REM  
Ends a `REM_BLOCK` comment block and returns to normal payload execution.  
## Keystroke Injection  
  
STRING  
Types the text that follows as keystrokes. Uppercase is handled automatically with `SHIFT` as needed. Trailing spaces may be omitted.  
  
STRINGLN  
Types the text that follows, then presses `ENTER`.  
  
STRING … END_STRING  
A multi-line string block that combines the lines into one continuous string without needing `STRING` on each line.  
Note: leading whitespace is stripped and newlines are ignored.  
  
STRINGLN … END_STRINGLN  
A multi-line string block that injects each line as written and presses `ENTER` after each line.  
Note: the first tab of indentation is stripped, but other formatting is preserved.  
  
  
## Cursor Keys  
  
UP / DOWN / LEFT / RIGHT  
Moves the cursor in the corresponding direction.  
  
UPARROW / DOWNARROW / LEFTARROW / RIGHTARROW  
Alternate names for the arrow keys.  
  
PAGEUP / PAGEDOWN  
Scrolls one page up or down.  
  
HOME / END  
Moves to the start or end of a line/document (behavior depends on context).  
  
INSERT  
Toggles insert/overwrite mode (behavior depends on app/OS).  
  
DELETE / DEL  
Deletes the character after the cursor (or selected content).  
  
BACKSPACE  
Deletes the character before the cursor.  
  
TAB  
Moves focus to the next UI element or inserts a tab character (context-dependent).  
  
SPACE  
Inserts a space character.  
  
  
## System Keys  
  
ENTER  
Confirms actions or inserts a new line (context-dependent).  
  
ESCAPE  
Cancels/backs out of dialogs or dismisses UI elements.  
  
PAUSE / BREAK  
Sends the Pause/Break key (rarely used; behavior depends on OS/app).  
  
PRINTSCREEN  
Triggers a screenshot action (behavior depends on OS configuration).  
  
MENU / APP  
Opens the context menu (similar to right-click).  
  
F1–F12  
Sends the function key specified.  
  
  
## Modifier Keys  
  
SHIFT  
Modifier used for uppercase letters and alternate symbols.  
  
ALT  
Modifier used for shortcuts and menu access.  
  
CONTROL / CTRL  
Modifier used for common shortcuts (copy, paste, etc.).  
  
COMMAND  
macOS modifier key (Command).  
  
WINDOWS / GUI  
Windows modifier key (Windows key / “GUI” key in DuckyScript).  
  
  
## Key + Modifier Combos  
  
CTRL SHIFT (etc.)  
Modifiers can be combined and used with other keys to form shortcuts (e.g., `CTRL SHIFT ESC`).  
  
CONTROL ALT DELETE / CTRL ALT DELETE  
Sends the classic secure attention sequence on Windows (behavior depends on context/OS).  
  
  
## Standalone Modifiers  
  
INJECT_MOD  
Allows injecting a modifier key by itself (e.g., pressing `WINDOWS` alone) by prefixing the modifier with `INJECT_MOD`.  
  
  
## Lock Keys  
  
CAPSLOCK  
Toggles caps lock state.  
  
NUMLOCK  
Toggles num lock state.  
  
SCROLLOCK  
Toggles scroll lock state (rarely used; may affect some apps).  
  
  
## Delays  
  
DELAY  
Pauses payload execution for the specified time in milliseconds. Useful for waiting on windows, prompts, or device enumeration.  
Note: minimum delay is typically 20ms, and timing can vary by host and `ATTACKMODE`.  
  
## Button Controls  
  
WAIT_FOR_BUTTON_PRESS  
Halts payload execution until the device button is pressed.  
  
BUTTON_DEF … END_BUTTON  
Defines a button handler that runs when the button is pressed during execution (unless another button command is currently controlling the button).  
  
DISABLE_BUTTON  
Disables the button handler set by `BUTTON_DEF`.  
  
ENABLE_BUTTON  
Re-enables the button handler set by `BUTTON_DEF`.  
  
  
## LED Controls  
  
LED_OFF  
Turns off all LED modes.  
  
LED_R  
Enables the red LED.  
  
LED_G  
Enables the green LED.  
  
  
## Attack Modes  
  
ATTACKMODE  
Sets what USB device type the Rubber Ducky emulates. If not specified first (excluding comments), it typically defaults to `HID`.  
Note: changing attack modes mid-payload may cause the target to re-enumerate the USB device.  
  
ATTACKMODE HID  
Emulates a keyboard (HID) for keystroke injection.  
  
ATTACKMODE STORAGE  
Emulates USB mass storage (flash drive).  
  
ATTACKMODE HID STORAGE  
Emulates both keyboard and mass storage.  
  
ATTACKMODE OFF  
Emulates no device (effectively “disconnects” from the host).  
  
VID_ / PID_  
Optional vendor and product IDs (must be used together) to spoof USB identity.  
  
MAN_ / PROD_ / SERIAL_  
Optional manufacturer/product/serial strings (must be used together) to spoof USB identity.  
  
SAVE_ATTACKMODE  
Saves the current `ATTACKMODE` configuration so it can be restored later.  
  
RESTORE_ATTACKMODE  
Restores the most recently saved `ATTACKMODE` configuration.  
  
  
## Constants  
  
DEFINE  
Defines a compile-time constant (macro-style replacement). Useful for reusable values like delays or text.  
  
  
## Variables  
  
VAR  
Declares a variable (prefixed with `$`). Variables commonly store unsigned integers (0–65535) and can also be used for boolean logic.  
  
  
## Operators  
  
Math Operators (=, +, -, * , /, %, ^)  
Used for assignment and arithmetic in expressions.  
  
Comparison Operators (== , !=, >, <, >=, <=)  
Used to evaluate conditions as true/false.  
  
Logical Operators (&&, ||)  
Used to combine expressions with AND/OR logic.  
  
Parentheses ( )  
Required to control precedence and make evaluation order explicit.  
  
Bitwise Operators (&, |, >>, <<)  
Performs bit-level operations on integer values.  
  
  
## Conditional Statements  
  
IF … END_IF  
Executes the block only if the condition evaluates to true.  
  
ELSE / ELSE IF  
Optional branches for alternate execution paths when the `IF` condition is false.  
  
  
## Loops  
  
WHILE … END_WHILE  
Repeats the block as long as the condition remains true.  
  
## Functions  
  
FUNCTION FUNCTIONNAME() … END_FUNCTION  
Defines a reusable block of code that can be called by name.  
  
RETURN  
A function may return a integer or boolean value which may also be evaluated.
  
## Randomization  
  
RANDOM_(lowercase_letter/uppercase_letterletter/number/special/char)
Injects random characters from a defined set (useful for test data and variability).  
  
$_ RANDOM_MIN / $_ RANDOM_MAX / $_ RANDOM_INT  
Sets bounds and reads a random integer within the specified range for use in variables and logic.
  
ATTACKMODE * RANDOM options  
Some `ATTACKMODE` identity fields can be randomized; use carefully because it may cause inconsistent host behavior.  
  
  
## Holding Keys  
  
HOLD  
Presses and holds the specified key until a matching `RELEASE` occurs.  
  
RELEASE  
Releases a key previously held with `HOLD`. Often paired with `DELAY` between hold and release.  
  
  
## Payload Control  
  
RESTART_PAYLOAD  
Stops execution and restarts the payload from the beginning.  
  
STOP_PAYLOAD  
Immediately stops payload execution.  
  
RESET  
Clears the keystroke buffer/state (useful for debugging stuck holds/modifiers).  
  
  
## Jitter  
  
$_ JITTER_ENABLED / $_ JITTER_MAX  
Enables keystroke timing variance and sets the maximum per-keystroke jitter (ms), based on the device seed value.  
  
  
## Payload Hiding (MicroSD)  
  
HIDE_PAYLOAD  
Hides payload files (e.g., `inject.bin`, `seed.bin`) from the MicroSD before enabling storage mode. Typically used while in `OFF` or `HID`.  
  
RESTORE_PAYLOAD  
Restores previously hidden payload files so they are visible again.  
  
  
## Lock Key Waits  
  
WAIT_FOR_CAPS_ON / WAIT_FOR_CAPS_OFF / WAIT_FOR_CAPS_CHANGE  
Pauses until caps lock reaches the specified state or is toggled.  
  
WAIT_FOR_NUM_ON / WAIT_FOR_NUM_OFF / WAIT_FOR_NUM_CHANGE  
Pauses until num lock reaches the specified state or is toggled.  
  
WAIT_FOR_SCROLL_ON / WAIT_FOR_SCROLL_OFF / WAIT_FOR_SCROLL_CHANGE  
Pauses until scroll lock reaches the specified state or is toggled.  
  
SAVE_HOST_KEYBOARD_LOCK_STATE  
Saves the current host-reported lock key states (LED state) for later restoration.  
  
RESTORE_HOST_KEYBOARD_LOCK_STATE  
Restores the saved lock key states so you don’t leave the user’s keyboard toggles changed.  
  
  
## Exfiltration (High-Level)  
  
EXFIL  
Writes variable data to a loot file on the device (for authorized lab/testing use). This is local capture, not a network transfer.  
  
Keystroke Reflection  
Uses lock key state changes as a signaling channel to store data back to the device (saved to `loot.bin`), where supported/configured.

Variable Exfiltration
Similarly, arbitrary variable data may be saved to the `loot.bin` file using the `EXFIL` command.