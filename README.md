# Working Progress...

<h1 align="center"> Android-Live-Templates </h1>

<div align="center">
  <img src="https://awesome.re/badge.svg" alt="Awesome Badge"/>
  <img src="https://img.shields.io/static/v1?label=%F0%9F%8C%9F&message=If%20Useful&style=style=flat&color=BC4E99" alt="Star Badge"/>
  <img src="https://img.shields.io/badge/Follow-%40code.fun-red?style=social&logo=instagram" alt="Instagram Badge"/>
</div>
<h5 align="center"> <i> A curated list of Android Live Templates </i> </h5>
<div align="center">
  <img src="https://badgen.net/github/stars/agamkoradiya/Android-Live-Templates" alt="Star Badge"/>
  <img src="https://badgen.net/github/forks/agamkoradiya/Android-Live-Templates" alt="Fork Badge"/>
  <img src="https://badgen.net/github/issues/agamkoradiya/Android-Live-Templates" alt="Issues Badge"/>
  <img src="https://badgen.net/github/prs/agamkoradiya/Android-Live-Templates" alt="PR Badge"/>
  <img src="https://badgen.net/github/contributors/agamkoradiya/Android-Live-Templates" alt="Contributors Badge"/>
  <img src="https://badgen.net/github/license/agamkoradiya/Android-Live-Templates" alt="License Badge"/>
</div>

# Content
  - [What is live template? 😮](#what-is-live-template-)
  - [How to *import all live templates* in 1 minute? 💥](#how-to-import-all-live-templates-in-1-minute-)
  - [CheatSheet for this repository 📄](#cheatsheet-)
      - [Adapter](#-adapter)
          - [adapter list](#adapter-list)
          - [adapter normal](#adapter-normal)
      - [View binding](#-view-binding)
          - [binding activity](#binding-activity)
          - [binding fragment](#binding-fragment)
      - [Retrofit library](#-retrofit-library)
          - [retofit instance](#retrofit-instance)
      - Room database
      - Dependency Injection
      - Drawable
      - XML
      - Util
      - Gradle dependency
  - How to create your own live template? 😊
  - Suggest me!  ✒️

---

## What is live template? 😮
<samp> Live Templates are code snippets that you can insert into your code by typing their abbreviation and pressing tab.
By using them, you can quickly and intelligently add frequently used code patterns and constructs to your code, letting the IDE do the tedious work for you. </samp>

## How to import all live templates in 1 minute? 💥
<img alt="How to import all live templates" src="assets/howToImport.gif"> </img>

## CheatSheet 📄

### 📌 Adapter
<br>

<div name="adapter-list">

>  <samp> adapter list </samp>
  
```kotlin 
class $FILE_NAME$ : androidx.recyclerview.widget.ListAdapter<$TYPE$, $FILE_NAME$.$HOLDER_NAME$ViewHolder>(DiffCallback()) {

    override fun onCreateViewHolder(parent: android.view.ViewGroup, viewType: Int): $HOLDER_NAME$ViewHolder {
        val binding =
            $BINDING$.inflate(
                android.view.LayoutInflater.from(parent.context),
                parent,
                false
            )
        return $HOLDER_NAME$ViewHolder(binding)
    }

    override fun onBindViewHolder(holder: $HOLDER_NAME$ViewHolder, position: Int) {
        val currentItem = getItem(position)
    }

    inner class $HOLDER_NAME$ViewHolder(private val binding: $BINDING$) :
        androidx.recyclerview.widget.RecyclerView.ViewHolder(binding.root) {}

    class DiffCallback : androidx.recyclerview.widget.DiffUtil.ItemCallback<$TYPE$>() {
        override fun areItemsTheSame(oldItem: $TYPE$, newItem: $TYPE$) =
            oldItem.id == newItem.id

        override fun areContentsTheSame(oldItem: $TYPE$, newItem: $TYPE$) =
            oldItem == newItem
    }
}
```
</div>
<br>

<div name="adapter-normal">

>  <samp> adapter normal </samp>
  
```kotlin
  class $FILE_NAME$ : androidx.recyclerview.widget.RecyclerView.Adapter<$FILE_NAME$.MyViewHolder>() {

    class MyViewHolder(itemView: android.view.View) : androidx.recyclerview.widget.RecyclerView.ViewHolder(itemView) {}

    override fun onCreateViewHolder(parent: android.view.ViewGroup, viewType: Int): MyViewHolder {
        return MyViewHolder(
            android.view.LayoutInflater.from(parent.context).inflate(R.layout.$LAYOUT$, parent, false)
        )
    }

    override fun getItemCount(): Int {
        TODO("Not yet implemented")
    }

    override fun onBindViewHolder(holder: MyViewHolder, position: Int) {
        TODO("Not yet implemented")
    }
}
```
</div>
<br>

### 📌 View Binding
<br>

<div name="binding-activity">

>  <samp> binding activity </samp>

```kotlin
class $FILE_NAME$ : androidx.appcompat.app.AppCompatActivity() {

    private lateinit var binding: $BINDING_LAYOUT$

    override fun onCreate(savedInstanceState: android.os.Bundle?) {
        super.onCreate(savedInstanceState)
        binding = $BINDING_LAYOUT$.inflate(layoutInflater)
        val view = binding.root
        setContentView(view)
    }
}
```
</div>
<br>

<div name="binding-fragment">

>  <samp> binding fragment </samp>

```kotlin
class $FILE_NAME$ : androidx.fragment.app.Fragment() {

    private var _binding: $BINDING_LAYOUT$? = null
    private val binding get() = _binding!!

    override fun onCreateView(
        inflater: android.view.LayoutInflater,
        container: android.view.ViewGroup?,
        savedInstanceState: android.os.Bundle?
    ): android.view.View {
        _binding = $BINDING_LAYOUT$.inflate(inflater, container, false)
        return binding.root
    }

    override fun onDestroyView() {
        super.onDestroyView()
        _binding = null
    }
}
```
</div>
<br>

### 📌 Retrofit Library
<br>

<div name="retrofit-instance">

>  <samp> retrofit instance </samp>

```kotlin
class $FILE_NAME$ {

    companion object {

        private val retrofit by lazy {
            val logging = okhttp3.logging.HttpLoggingInterceptor()
            logging.setLevel(okhttp3.logging.HttpLoggingInterceptor.Level.$TYPE$)
            val client = okhttp3.OkHttpClient.Builder()
                .addInterceptor(logging)
                .build()
            retrofit2.Retrofit.Builder()
                .baseUrl($BASE_URL$)
                .addConverterFactory(retrofit2.converter.gson.GsonConverterFactory.create())
                .client(client)
                .build()
        }

        val api by lazy {
            retrofit.create($API_NAME$::class.java)
        }
    }
    
}
```
</div>
<br>
