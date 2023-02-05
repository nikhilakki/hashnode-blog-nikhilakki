# NoJS tools for creating Dashboards using Python

## Motivation for this post

I recently built a dashboard for client work, the dashboard needed to be offline as the data was sensitive, and we didn't have the time to request a cloud environment (*to host it as a web app in the client's environment; it would have come with its own set of challenges of handling auth and access management*).

In simple words, the dashboard needed to be more like an interactive report that can be shared as a document or HTML page.

tl;dr - We used Datapane!

### My top three picks

1. Dash by Plotly
    
2. Steamlit
    
3. Datapane
    

### **Dash**

Dash is a software platform for building interactive web-based applications with Python. It is designed to make it easy to build and deploy interactive dashboards and applications that can be used to display real-time data, analyze and visualize data, and facilitate decision-making.

With Dash, developers can use Python to build interactive applications that include a variety of interactive elements, such as graphs, charts, tables, and maps. Dash applications can be deployed to the web and accessed from any device with a web browser.

One of the key features of Dash is its ability to interact with a wide range of data sources and visualization libraries. Developers can use Dash to pull in data from a variety of sources, including databases, APIs, and local files, and can use libraries like Plotly and Matplotlib to create custom visualizations.

Overall, Dash is a powerful tool for data scientists, analysts, and developers who want to build interactive web-based applications for data visualization and analysis. It is particularly useful for building dashboards and applications that can be used to track key performance indicators (KPIs) and facilitate decision-making.

> "Use **Dash** if you need an interactive dashboard with real-time data updates and the intended audience is non-technical, Dash is built with Flask so it is quite extensible and comes with decent Enterprise support!"

### Streamlit

Streamlit is an open-source software platform for building interactive web applications with Python. It is designed to make it easy for developers to build and deploy interactive data visualization and analysis tools, machine learning models, and other applications that can be accessed from a web browser.

With Streamlit, developers can use Python to build interactive applications that include a variety of interactive elements, such as graphs, charts, tables, and maps. Streamlit applications can be deployed to the web and accessed from any device with a web browser.

One of the key features of Streamlit is its simplicity and ease of use. It has a user-friendly interface that allows developers to build applications quickly and easily, without the need to write complex HTML or JavaScript code. Streamlit also has several built-in features that make it easy to build interactive applications, including the ability to add buttons, sliders, and text input fields to allow users to interact with the application.

Overall, Streamlit is a powerful tool for data scientists, analysts, and developers who want to build interactive web-based applications for data visualization and analysis. It is particularly useful for building standalone applications that can be used to explore and analyze data and can be a useful addition to any data scientist's toolkit.

> "We use **Streamlit** if the dashboard needs real-time data updates and the intended audience are devs/peers. The dev time is faster than Dash based on our experience but is comparatively less extensible. Streamlit Cloud version should help remove most of the limitations"

### Datapane

Datapane is a software platform that allows data scientists and analysts to share their work with others in an interactive and easily digestible format. It is designed to make it easy to create interactive reports, dashboards, and notebooks that can be shared with colleagues, stakeholders, and the general public.

With Datapane, users can import data from a variety of sources, including local files, databases, and cloud storage services. They can then use a variety of tools and libraries, such as Python, R, and SQL, to analyze and visualize the data. The results of their work can be shared as interactive reports, dashboards, and notebooks that can be viewed and interacted with in a web browser.

Datapane is particularly useful for data teams that want to share their work with a wider audience, as it allows them to create interactive and visually appealing reports that can be easily understood by non-technical users. It is also useful for teams that want to collaborate on data projects, as it allows users to share and collaborate on reports and notebooks in real time.

> "Use **Datapane** if you want to share the dashboard as a static HTML report! Real-time data updates are out of scope for this one!"

### How do they compare to each other?

**Streamlit** and **Dash** are both platforms for creating interactive web-based applications with Python. They are often used for data visualization and analysis and can be used to build a wide range of applications, including dashboards, reports, and machine-learning tools.

Like Datapane, Streamlit and Dash allow users to import data from a variety of sources and use Python to analyze and visualize the data. They also both have a focus on creating interactive and visually appealing applications that can be easily understood by non-technical users.

One key difference between the three platforms is the way they are used. Streamlit is primarily a tool for creating standalone applications, whereas Dash is focused on building interactive dashboards and applications that can be embedded into other websites or applications. Datapane, on the other hand, is more geared towards creating interactive reports and notebooks that can be shared with a wide audience and has features specifically designed for collaboration and sharing.

Overall, the choice between the three platforms will depend on the specific needs and goals of your project. If you are looking to build a standalone application, Streamlit may be the best choice. If you are looking to build an interactive dashboard that can be embedded in another application, Dash might be the better option. And if you are looking to create interactive reports and notebooks that can be easily shared with a wide audience, Datapane could be a good fit.

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Framework</strong></p></td><td colspan="1" rowspan="1"><p><strong><mark>Dash</mark></strong></p></td><td colspan="1" rowspan="1"><p><strong><mark>Streamlit</mark></strong></p></td><td colspan="1" rowspan="1"><p><strong><mark>Datapane</mark></strong></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Ease of use</strong></p></td><td colspan="1" rowspan="1"><p>⭐⭐</p></td><td colspan="1" rowspan="1"><p>⭐⭐⭐</p></td><td colspan="1" rowspan="1"><p>⭐⭐⭐</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Hosting</strong> <strong>Method</strong></p></td><td colspan="1" rowspan="1"><p>Like a web app</p></td><td colspan="1" rowspan="1"><p>Like a web app</p></td><td colspan="1" rowspan="1"><p>Static HTML</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Library Support</strong></p></td><td colspan="1" rowspan="1"><p>Ploty, Bokeh and other major plotting libraries</p></td><td colspan="1" rowspan="1"><p>Ploty, Bokeh and other major plotting libraries</p></td><td colspan="1" rowspan="1"><p>Ploty, Bokeh and other major plotting libraries</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Enterprise Support</strong></p></td><td colspan="1" rowspan="1"><p>Yes</p></td><td colspan="1" rowspan="1"><p>Yes; with Cloud Version</p></td><td colspan="1" rowspan="1"><p>Yes with cloud Version</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Customization</strong> (<strong>Frontend</strong>)</p></td><td colspan="1" rowspan="1"><p>⭐⭐⭐</p></td><td colspan="1" rowspan="1"><p>⭐⭐⭐</p></td><td colspan="1" rowspan="1"><p>⭐⭐⭐</p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>Customization</strong> (<strong>Backend</strong>)</p></td><td colspan="1" rowspan="1"><p>⭐⭐⭐</p></td><td colspan="1" rowspan="1"><p>⭐⭐</p></td><td colspan="1" rowspan="1"><p>N/A</p></td></tr></tbody></table>

### Conclusion

We used Datapane; as stated in the section above, the data was sensitive and the client was expecting the data analysis in a report format. In the end, when we shared the dashboard file, the client was impressed, they were expecting just a PowerPoint presentation; the interactive dashboard was a pleasant surprise.

**What will you build? Let me know in the comments section!**