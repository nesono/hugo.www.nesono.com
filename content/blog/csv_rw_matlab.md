---
title:       "Read and Write CSV Files with Matlab with Headers"
type:        blog
date:        2012-11-09
draft:       false
promote:     true
sticky:      false
aliases:     [ node/415 ]
blog categories: [ "programming", "matlab" ]
flattr username: [ "nesono" ]

---

This is a follow up post of a previous [one][1] just using Matlab instead of Python.
In the following paragraphs, I will show my way of reading and writing CSV files using Matlab.
If you happen to know a better or more elegant solution, please drop a comment!

## Reading CSV Files with Matlab

The following Matlab function reads a CSV file with the header as a string vector and the data as numeric matrix. Note that non-numerical data returns NaN.

```matlab
function [h,m] = csvreadh( filename, delim )
%CSVREADH Read a comma separated value file with header.
%   [H,M] = CSVREADH('FILENAME') reads a comma separated value formatted file
%   FILENAME.  The result data is returned in M, the header in H. 
%   The file can only contain numeric values as data and a string for 
%   the header.

% Validate input args
if nargin==0
    error(nargchk(1,1,nargin,'struct')); 
end

% Get Filename
if ~ischar(filename)
    error('csvreadh:FileNameMustBeString', ...
        'Filename must be a string.'); 
end

% Make sure file exists
if exist(filename,'file') ~= 2 
    error('csvreadh:FileNotFound',...
    'File not found.');
end

if nargin==1
    delim = ',';
end

% open input file
file = fopen( filename );
line = fgetl( file );
h = regexp( line, delim, 'split' );

m = [];
% this is not quick for sure, but works
while 1
    line = fgetl( file );
    if ~ischar(line), break, end
    m = [m; str2double(regexp( line, ',', 'split' ))];
end

fclose(file);
```

## Writing CSV Files with Matlab

The following snippet provides a function to write a csv file in Matlab:

```matlab
function csvwriteh( filename, data, header )
%CVSWRITEH write matrix to a csv file with header
% CVSWRITEH( FILENAME, DATA, HEADER )
% function to write a csvfile with a header
% input parameters:
%   FILENAME: filename for csv output file
%   DATA:     matrix with data for csv file
%   HEADER:   cell array with names per column

%% check parameters
% filename parameter
if exist( 'filename', 'var' )
    if ~ischar( filename )
        error('filename not char')
    end
else
    error('filename does not exists')
end
% data parameter
if exist( 'data', 'var' )
    if ~isnumeric( data )
        error('data not numeric')
    end
else
    error('data does not exist')
end
% header parameter
if exist( 'header', 'var' )
    if ~iscellstr( header )
        error('header no cell str')
    end
else
    error('header does not exist')
end

% check dimensions of data and header
[drow dcol] = size (data);
[hrow hcol] = size (header);
if hcol ~= dcol
    error( 'header not of same length as data (columns)' )
end

% open file
outid = fopen (filename, 'w+');

% write header
for idx = 1:hcol
    fprintf (outid, '%s', header{idx});
    if idx ~= hcol
        fprintf (outid, ',');
    else
        fprintf (outid, '\n' );
    end
end
% close file
fclose(outid);

% write data
dlmwrite (filename, data, '-append' );
```


That's it again.  
Cheers,

iss

[1]: https://www.nesono.com/node/414 "Read and Write CSV files with Python"
