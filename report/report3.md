### Designing the Optimal Employee Experience (For Employers' Wallets)

##### Joey Maalouf

_Medium_, an online journal with a dedicated data science category, published an interesting dataset on _Kaggle_ about employee conditions and whether or not a given employee quit their job at that company<sup>[1]</sup>. It contains 15,000 responses with a variety of potentially useful fields, such as the employee's pay grade, number of projects, and average monthly hours.

The obvious thing to do, with access to all of these features and a categorical result variable, is to train a logistic regression model. With so many different categories, it's hard to really say what primarily drives an employee to quit their job; for that, we can look at the coefficient parameters of our trained model. We can discount any of the features with a p-value greater than 0.05 as not necessarily statistically significant, and we don't want to risk coming to any false or unsupported conclusions.

![Figure 1: Logistic Regression Model Coefficients](../img/logreg_coeffs.png)

Figure 1 shows the coefficients of the features in the logistic regression model that can be considered statistically significant, where negative values correspond to conditions in which employees tend to stay and positive values correspond to conditions that make employees want to leave. As we might have suspected, satisfaction level is _extremely_ important to keeping your employees, and the lower the pay grade, the more likely they are to leave. Additionally, a longer employment duration is a big indicator of quitting likelihood; however, this is almost certainly due to the tendency we have of transitioning between jobs over time until we retire.

It's quite interesting that employees are _less_ likely to leave a company if they've suffered a work accident in their time there; my theory is that they tend to receive a benefits package or something similar to convince them to stay as a happy worker and not sue the company. Also of note is the relatively small part the employee's department plays, especially when compared to "major events" like having a work accident or not being promoted. However, within the comparison between departments, human resources workers are most likely to leave, while support staff and miscellaneous employees are least likely to quit.

Now we have the potential to solve an interesting problem: how can employers best optimize their employee conditions to minimize attrition rate while keeping costs low? Well, fortunately enough, our logistic regression model can predict the likelihood of an employee quitting given their current conditions, as well as how that might vary depending on how those conditions change.

To demonstrate, we can look at some theoretical typical employee; someone working 40-hour weeks on a few different projects, with a medium salary and mid-level evaluations and satisfaction. He's been working sales for a few years and hasn't gotten a promotion yet. This individual, according to our model, has a 24.43% chance of quitting before the company lets him go. If we want to lower that, we can look at changing a variety of things; one feature in particular that isn't likely to cost much is the employee's satisfaction level, which can probably change with simple quality of life fixes around the office.

![Figure 2: Sample Employee](../img/sample_employee.png)

As Figure 2 shows, even with all other variables like pay grade and working hours held constant, an employee's quit chance can vary by dozens of percent based solely on how much he enjoys being in the office. Alternatively, an employer with a particularly flexible moral compass might opt not to target his employee's satisfaction level, but instead arrange a work-related accident. This would drop our sample employee's probability of leaving to a mere 6.54% and make them much more likely to continue working for the company, for just the cost of a reparations package.

We can also extend the predicted quitting probability for some given set of conditions to be the total attrition rate of a company, department, or other group where all employees exist in conditions similar to the ones given; this allows employers to design their department environments to minimize expenses with a maximum allowable attrition rate in mind. [TODO: talk about trends for each feature here, basically reference the feature coefficients.]

<sup>[1] [Human Resources Analytics: Why are our best and most experienced employees leaving prematurely?](https://www.kaggle.com/ludobenistant/hr-analytics)
<br>
[Notebook Source](https://github.com/joeylmaalouf/HR-analytics/blob/master/report/report3.ipynb)</sup>
