1)
rotate.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class rotate : MonoBehaviour
{
    public float moveSpeed;

    // Start is called before the first frame update
    void Start()
    {
        moveSpeed = 5f;
    }

    // Update is called once per frame
    void Update()
    {
        transform.Rotate(1,0,0);
 
    }
}

Or 

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using System;

public class rotate : MonoBehaviour
{
    public float moveSpeed;

    // Start is called before the first frame update
    void Start()
    {
        moveSpeed = 500f;
    }

    // Update is called once per frame
    void Update()
    {
        //Vector3.up is Vector3(0, 1, 0) rotate along Y axis
        if (Input.GetKey(KeyCode.Z))
            transform.Rotate(Vector3.up * moveSpeed * Time.deltaTime);

        if (Input.GetKey(KeyCode.X))
            transform.Rotate(-Vector3.up * moveSpeed * Time.deltaTime);
    }
}

move.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class move : MonoBehaviour
{
    public float moveSpeed;

    // Start is called before the first frame update
    void Start()
    {
        moveSpeed = 5f;
    }

    // Update is called once per frame
    void Update()
    {
        
        transform.Translate(moveSpeed * Input.GetAxis("Horizontal") * Time.deltaTime, 0f, moveSpeed * Input.GetAxis("Vertical") * Time.deltaTime);
    }
}
scale.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class scale : MonoBehaviour
{
    // Start is called before the first frame update
    public float size=0.1f;
    // public Vector3 scale change d
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if(Input.GetKey("e"))
        transform.localScale+=new Vector3(size,0,0);
        else if(Input.GetKey("d"))
        transform.localScale-=new Vector3(size,0,0);
        else if(Input.GetKey("r"))
        transform.localScale+=new Vector3(0,size,0);
        else if(Input.GetKey("f"))
        transform.localScale-=new Vector3(0,size,0);
        else if(Input.GetKey("t"))
        transform.localScale+=new Vector3(0,0,size);
        else if(Input.GetKey("g"))
        transform.localScale-=new Vector3(0,0,size);
    }
}
prgrm 2
bounce.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class BallCollision : MonoBehaviour
{
    public float moveSpeed;
    private Rigidbody rbody;
    private Renderer rend; 
    // Start is called before the first frame update
    void Start()
    {
        moveSpeed = 15f;
        rbody = GetComponent<Rigidbody>();
        rend = GetComponent<Renderer>();
    }

    // Update is called once per frame
    void Update()
    {
        float inputx = Input.GetAxis("Horizontal");
        float inputz = Input.GetAxis("Vertical");
        float movex = inputx * moveSpeed * Time.deltaTime;
        float movez = inputz * moveSpeed * Time.deltaTime;
        rbody.transform.Translate(-movex,0f,-movez);
    }

    private void OnCollisionEnter(Collision col) {
        if(col.collider.name == "Front") {
            rend.material.color = Color.green;
        }
        else if(col.collider.name == "Left" || col.collider.name == "Right") {
            rend.material.color = Color.blue;
        }
        else if(col.collider.name == "Top" || col.collider.name == "Bottom") {
            rend.material.color = Color.red;
        }
    }
}

Or 

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class bounce_2 : MonoBehaviour
{
    public float moveSpeed = 100f;
    private Rigidbody rbody;
    private Renderer rend;
    // Start is called before the first frame update
    void Start()
    {
        rbody = GetComponent<Rigidbody>();
        rend = GetComponent<Renderer>();
    }

    // Update is called once per frame
    void Update()
    {
        float inputX = Input.GetAxis("Horizontal");
        float inputZ = Input.GetAxis("Vertical");
        float moveX = inputX * moveSpeed * Time.deltaTime;
        float moveZ = inputZ * moveSpeed * Time.deltaTime;
        rbody.AddForce(moveX, 0f, moveZ,ForceMode.Impulse);
    }
    private void OnCollisionEnter(Collision col)
    {
        if (col.collider.name == "5")
        {
            rend.material.color = Color.blue;
        }
        else if (col.collider.name == "2")
        {
            rend.material.color = Color.green;
        }
        else if (col.collider.name == "3")
        {
            rend.material.color = Color.red;
        }
        else if (col.collider.name == "4")
        {
            rend.material.color = Color.yellow;
        }
    }
}



3)
bounce.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class bounce : MonoBehaviour
{
    // Start is called before the first frame update
    public float force =600f;
    void Start()
    {
       GetComponent<Rigidbody>().velocity=new Vector3(5,5,0);
    }


    private void OnCollisionEnter(Collision col)
    {
        if(col.collider.name=="Cube (3)")
        {
            GetComponent<Rigidbody>().AddForce(Random.Range(-5f, 5f) * 5, 0f, 0f,ForceMode.Impulse);
        }
    }
}
Or

Bounce randomness.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ball1 : MonoBehaviour
{
    // Start is called before the first frame update
    private Rigidbody r;
    void Start()
    {
        r = GetComponent<Rigidbody>();
        r.velocity = new Vector3(3f, 0f, 5f);
    }

    // Update is called once per frame
    void Update()
    {

        
    }

    private void OnCollisionEnter(Collision col)
    {
        if(col.collider.name=="paddle")
        {
            r.AddForce(Random.Range(-1f, 1f) * 5, 0f, Random.Range(5f, 10f),ForceMode.Impulse);
        }
    }
}



paddle.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class paddle : MonoBehaviour
{
    public float moveSpeed;

    // Start is called before the first frame update
    void Start()
    {
        moveSpeed = 5f;
    }

    // Update is called once per frame
    void Update()
    {
        transform.Translate(moveSpeed * Input.GetAxis("Horizontal") * Time.deltaTime, 0f, 0f);
    }
}
4th(lowlypoly,free trees)
move.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class move_4 : MonoBehaviour
{
    // Start is called before the first frame update
    public float movespeed;
    void Start()
    {
        movespeed = 5f;
    }

    // Update is called once per frame
    void Update()
    {
        transform.Translate(0f, 0f, movespeed * Time.deltaTime * Input.GetAxis("Vertical"));
        transform.Rotate(0f, movespeed * Time.deltaTime * Input.GetAxis("Horizontal"), 0f);
    }
}


6th
appear
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class appear : MonoBehaviour
{
    public GameObject car;
    public GameObject bus;

    void start()
    {
        bus.SetActive(false);
        car.SetActive(false);
    }

    public void openBus()
    {
        bus.SetActive(true);
        car.SetActive(false);
    }
    public void openCar()
    {
        car.SetActive(true);
        bus.SetActive(false);
    }
}
7th
light.cs

using UnityEngine;

public class color : MonoBehaviour
{
    // Start is called before the first frame update
    public Renderer rend;
    public Light lightComp;
    public Color[] colors = new Color[] { new Color(0,1,0,1), new Color(1,0,0,1), new Color(1,1,1,1), new Color(0,0,1,1) };
    public int index = 0;
    void Start()
    {
        Debug.Log(Color.blue);
        rend = gameObject.GetComponent<Renderer>();
        lightComp = GetComponent<Light>();
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKey(KeyCode.Tab) || Input.GetKey(KeyCode.Mouse0))
        {
            index = (index + 1) % 4; 
            lightComp.color = colors[index];
            rend.material.color = colors[index];
        }
    }
}




8th
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class shoot : MonoBehaviour
{
    public float movespeed = 10f;
    void Update()
    {
        transform.Rotate(0f, 0f, -Input.GetAxis("Horizontal")* movespeed * Time.deltaTime);
        if(Input.GetKey(KeyCode.Space))
        {
            Debug.DrawRay(transform.position, transform.TransformDirection(Vector2.up) * 20f, Color.red);
            RaycastHit2D hit = Physics2D.Raycast(transform.position, transform.TransformDirection(Vector2.up), 20f);
            if (hit)
            {
                Debug.Log("hit"+hit.collider.name);
                hit.transform.GetComponent<SpriteRenderer>().color = Color.green;
            }
        }
    }
}





9th-https://weeklyhow.com/loading-bar-screen-in-unity/
Level Manager.cs
using System.Collections;
using UnityEngine;
using UnityEngine.SceneManagement;
using UnityEngine.UI;
public class LevelManager : MonoBehaviour
{
    public GameObject loadingPanel;
    public Slider loadingBar;
    public Text loadingText;
    public void LoadLevel (string levelName)
    {
        StartCoroutine(LoadSceneAsync(levelName));//waits till yeild return null
    }
    IEnumerator LoadSceneAsync ( string levelName )
    {
        loadingPanel.SetActive(true);
        AsyncOperation op = SceneManager.LoadSceneAsync(levelName);
        while ( !op.isDone )
        {
            Debug.Log("0");
            float progress = Mathf.Clamp01(op.progress / .9f);
            loadingBar.value = progress;
            loadingText.text = progress * 100f + "%";
            op.allowSceneActivation=false;
            loadingText.text="Press F to continue";
            if(Input.GetKeyDown(KeyCode.F))
            op.allowSceneActivation=true;
            yield return null;
        }
    }
}

or

using System.Collections;
using UnityEngine;
using UnityEngine.SceneManagement;
using UnityEngine.UI;
public class LevelManager : MonoBehaviour
{
    public GameObject loadingPanel;
    public Slider loadingBar;
    public Text loadingText;
    public void LoadLevel (string levelName)
    {
        StartCoroutine(LoadSceneAsync(levelName));//waits till yeild return null
    }
    IEnumerator LoadSceneAsync ( string levelName )
    {
        loadingPanel.SetActive(true);
        loadingText.text = "0%";
        yield return StartCoroutine(Wait2Seconds());
        loadingBar.value = 0.5f;
        loadingText.text = "50%";
        yield return StartCoroutine(Wait2Seconds());
        AsyncOperation op = SceneManager.LoadSceneAsync(levelName);
        while (!op.isDone)
        {
            
            float progress = Mathf.Clamp01(op.progress / .9f);
            loadingBar.value = progress;
            if (progress * 100f > 51f)
            {
                loadingText.text = progress * 100f + "%";
            }
            yield return null;
        }
    }
    IEnumerator Wait2Seconds()
    {
        yield return new WaitForSeconds(2f);
    }
}



10th
sound.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class buttoncontrol : MonoBehaviour
{
    // Start is called before the first frame update
    public AudioSource horn,desc;
    bool flag;
    void Start()
    {
        flag=false;
    }

    // Update is called once per frame
    void Update()
    {
        
    }
    public void horning()
    {
        horn.Play();
    }
    public void describing()
    {
        
        if(flag)
        desc.Play();
        if(!flag)
        desc.Pause();
        flag=!flag;
    }


}
