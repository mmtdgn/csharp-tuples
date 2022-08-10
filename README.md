<!--
  Copyright (c) 2022 Mehmet

  Written by Mehmet Doğan <mmt.dgn.6634@gmail.com>, august 2022
-->
# C# Tuples
Example usages for tuples.
  
### Example
```c
public class TuplesExample : MonoBehaviour
{
    IEnumerator Start()
    {
        Tuples_Field();
        yield return new WaitForSeconds(1f);
        Tuples_Method();
    }

    private void Tuples_Field()
    {
        (string, float) t1 = ("Hello world", 3.1f);
        Debug.Log($"Tuple with string element : {t1.Item1}\n float element {t1.Item2}.");

        (double Sum, int Count) t2 = (4.5, 3);
        Debug.Log($"Sum of {t2.Count} elements is {t2.Sum}.");
    }
    private void Tuples_Method()
    {
        #region  Example1
        (string first, string second) ParseFirstAndLastName(string name)
        {
            if (string.IsNullOrEmpty(name))
            {
                throw new ArgumentNullException(nameof(name));
            }

            int indexOfFirstSpace = name.IndexOf(' ');
            return (name.Substring(0, indexOfFirstSpace), name.Substring(indexOfFirstSpace));
        }

        Debug.Log($"Tuples Example: String Parser output => {ParseFirstAndLastName("MD Games")}");
        Debug.Log($"Tuples Example: String Parser output => {ParseFirstAndLastName("Unity Engine")}");
        #endregion

        #region  Example2
        (int roundedValue, float realValue) RoundToNearestInteger(float value)
        {
            return ((int)Mathf.Round(value), value);
        }

        Debug.Log($"Tuples Example: rounded float output => {RoundToNearestInteger(4.2f)}");
        Debug.Log($"Tuples Example: rounded float output => {RoundToNearestInteger(6.7f)}");
        #endregion
    }

}
```
<summary><b>Screenshot</b></summary>
  
<img src="/.github/Screenshots/Screenshot_1.png">
