using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public float Speed = 1f;

    // Start is called before the first frame update
    void Start()
    {
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKey(KeyCode.RightArrow))
        {
            transform.Translate(Speed * Time.deltaTime * Vector2.right);
        }

        if (Input.GetKey(KeyCode.LeftArrow))
        {
            transform.Translate(Speed * Time.deltaTime * Vector2.left);
        }

        if (Input.GetKey(KeyCode.UpArrow))
        {
            transform.Translate(Speed * Time.deltaTime * Vector2.up);
        }

        if (Input.GetKey(KeyCode.DownArrow))
        {
            transform.Translate(Speed * Time.deltaTime * Vector2.down);
        }
    }

    private void OnTriggerEnter2D(Collider2D otherObject)
    {
        if (otherObject.gameObject.tag == "cookie")
        {
            Destroy(otherObject.gameObject);
        }

        if (otherObject.gameObject.tag == "Enemy")
        {
            transform.position = new Vector3(0f, -4f, 0f);
        }

        if (otherObject.gameObject.name == "Exit")
        {
            Speed = 0;
            GetComponent<CircleCollider2D>().enabled = false;
            transform.position = new Vector3(0f, 0f, 0f);
            transform.localScale = new Vector3(5f, 5f, 5f);
        }
    }

}
