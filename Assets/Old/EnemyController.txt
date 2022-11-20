using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyController : MonoBehaviour
{
    public float Speed = 1f;
    float directionalSpeed;

    // Start is called before the first frame update
    void Start()
    {
        directionalSpeed = Speed;
    }

    // Update is called once per frame
    void Update()
    {
        transform.Translate(directionalSpeed * Time.deltaTime * Vector2.right);
    }

    private void OnTriggerEnter2D(Collider2D otherObject)
    {
        if (otherObject.name == "LeftWall") directionalSpeed = Speed;
        else if (otherObject.name == "RightWall") directionalSpeed = -Speed;
    }
}
