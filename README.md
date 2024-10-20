using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerJump : MonoBehaviour
{
    public float jumpForce = 5f; // قوة القفز
    private bool isGrounded; // للتحقق إذا كان اللاعب على الأرض
    public Transform groundCheck; // نقطة للتحقق من الأرض
    public float checkRadius = 0.2f; // نصف القطر للتحقق من الأرض
    public LayerMask groundLayer; // لتحديد طبقة الأرض
    
    private Rigidbody2D rb;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>(); // الحصول على المكون RigidBody2D
    }

    void Update()
    {
        isGrounded = Physics2D.OverlapCircle(groundCheck.position, checkRadius, groundLayer); // التحقق من إذا كان اللاعب على الأرض

        // إذا كان اللاعب على الأرض وضغط على زر القفز
        if (isGrounded && Input.GetKeyDown(KeyCode.Space))
        {
            rb.velocity = Vector2.up * jumpForce; // تطبيق قوة القفز
        }
    }
}
