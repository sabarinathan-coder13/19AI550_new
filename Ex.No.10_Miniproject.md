# Ex.No: 10  Implementation of 3D game Coin Collector
### DATE:  31.08.2026                                                                          
### REGISTER NUMBER : 212225230231
### AIM: 
To develop a game Coin Collector 3Din Unity 
## Algorithm:
```
1.Start the game.
2.Create the player, ground, coins, obstacles, and finish point.
3.Set the player's initial position, speed, health, and score.
4.Read the player's keyboard input:
W / Up → Move forward
S / Down → Move backward
A / Left → Move left
D / Right → Move right
Space → Jump
5.Move the player according to the input.
6.Continuously check for collision:
   ->If the player touches a coin, increase the score and remove the coin.
   ->If the player hits an obstacle, decrease health.
7.Display the score and health on the screen.
8.If health becomes 0, display Game Over.
9.If the player reaches the finish point, display You Win with the final score.
10.Provide a Restart option to play again.
11.End the game.
```  
## Program:
### Main Player Script:
```
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float speed = 5f;
    public float jump = 7f;

    Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        float x = Input.GetAxis("Horizontal");
        float z = Input.GetAxis("Vertical");

        Vector3 move = new Vector3(x, 0, z);
        transform.Translate(move * speed * Time.deltaTime);

        if (Input.GetKeyDown(KeyCode.Space))
            rb.AddForce(Vector3.up * jump, ForceMode.Impulse);
    }
}
```
### Coin Script
```
using UnityEngine;

public class Coin : MonoBehaviour
{
    void Update()
    {
        transform.Rotate(0, 100 * Time.deltaTime, 0);
    }

    void OnTriggerEnter(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            GameManager.score++;
            Destroy(gameObject);
        }
    }
}
```
### GameManager
```
using UnityEngine;
using UnityEngine.UI;

public class GameManager : MonoBehaviour
{
    public static int score = 0;
    public Text scoreText;

    void Update()
    {
        scoreText.text = "Score: " + score;
    }
}
```
## Output:

<img width="1600" height="687" alt="WhatsApp Image 2026-09-16 at 9 51 34 AM" src="https://github.com/user-attachments/assets/03945892-6077-44d6-b9f3-0b21f66b964a" />

<img width="1600" height="680" alt="WhatsApp Image 2026-09-16 at 9 51 32 AM" src="https://github.com/user-attachments/assets/0692a3af-5126-43a6-bbad-b0de7e764bfa" />

<img width="1600" height="1084" alt="WhatsApp Image 2026-09-16 at 9 51 34 AM (1)" src="https://github.com/user-attachments/assets/9a9d2d89-8d11-4a39-8261-7f78bf766230" />

<img width="1600" height="1084" alt="WhatsApp Image 2026-09-16 at 9 51 33 AM" src="https://github.com/user-attachments/assets/eb56e6df-c4fc-4bec-b686-bfbfec929e52" />

<img width="1600" height="999" alt="WhatsApp Image 2026-09-16 at 9 51 35 AM" src="https://github.com/user-attachments/assets/d6aa7e9c-44ef-44d6-adcb-f8a63840d884" />

## Result:
Thus, the game was successfully developed using Unity and implemented with basic AI technology for interactive gameplay.

