class Solution 
{
    public int compress(char[] chars) 
    {
        int index = 0;
        int start = 0;
        while(start < chars.length)
        {
            int end = start;
            while(end < chars.length && chars[start] == chars[end])
            {
                end++;
            }
            int count = end - start;
            chars[index++] = chars[start];
            if(count >= 2)
            {
                char ans[] = Integer.toString(count).toCharArray();
                for(char ch : ans)
                {
                    chars[index++] = ch;
                }
            }
            start = end;
        }
        return  index;
    }
}
